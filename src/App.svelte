<script>
  import { onMount } from 'svelte'
  import Keyboard from './lib/Keyboard.svelte'
  import Letter from './lib/Letter.svelte'
  import Gallow from './lib/Gallow.svelte'

  let word = ''
  let splitWord = []
  let guesses = 6
  let wrongGuesses = 0
  let wrongLetters = []
  let correctGuesses = 0
  let correct
  let gameWon = false
  let gameLost = false
  let disabledKeys = []

  const getRandomWord = async () => {
    splitWord = []
    correctGuesses = 0
    wrongGuesses = 0
    wrongLetters = []
    disabledKeys = []
    gameWon = false
    gameLost = false
    const res = await fetch(
      'https://random-word-api.herokuapp.com/word?number=1',
    )
    let json = await res.json()
    word = json[0]
    for (let i = 0; i < word.length; i++) {
      splitWord = [...splitWord, { letter: word[i], show: false }]
    }
  }
  const makeGuess = (guess) => {
    splitWord.forEach((letter, i) => {
      if (guess === letter.letter) {
        correctGuesses = correctGuesses + 1
        splitWord[i] = { letter: letter.letter, show: true }
        disabledKeys = [...disabledKeys, guess]
        console.log(`correct guesses ${correctGuesses}`)
        if (correctGuesses === splitWord.length) {
          console.log('you win')
          gameWon = true
        }
        correct = true
      }
    })
    if (!correct) {
      wrongGuesses = wrongGuesses + 1
      wrongLetters = [...wrongLetters, guess]
      disabledKeys = [...disabledKeys, guess]
      console.log(wrongLetters)
      if (wrongGuesses === guesses) {
        console.log('you lose')
        gameLost = true
      }
    }
    correct = false
  }
  onMount(() => {
    getRandomWord()
  })
</script>

<main>
  <button on:click={getRandomWord}>Get new word</button>
  {#if gameWon}
    <h1>You win!<br />Get a new word!</h1>
  {/if}
  {#if gameLost}
    <h1>You lose,<br />the word was<br /> '{word}'.</h1>
  {/if}
  <div class="wrong-guesses">
    {#each wrongLetters as w}
      {w}
    {/each}
  </div>

  <Gallow {wrongGuesses} />
  <div class="letter-grid">
    {#each splitWord as letter}
      <Letter bind:show={letter.show} letter={letter.letter} />
    {/each}
  </div>
  <Keyboard
    bind:disabledKeys
    on:key={(e) => makeGuess(e.detail.key.key.toLowerCase())}
  />
</main>

<style lang="scss">
  main {
    font-family: monospace;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    min-height: 100vh;
    padding: 1em;
    position: relative;
  }
  h1 {
    position: absolute;
    left: 1rem;
    top: 4rem;
  }
  button {
    align-self: flex-start;
  }
  .letter-grid {
    display: flex;
    gap: 0.5em;
    margin-top: 16rem;
  }
  .wrong-guesses {
    position: absolute;
    top: 12rem;
    left: 1rem;
    font-size: clamp(0.5rem, 2.5vmin, 1.5rem);
  }
</style>
