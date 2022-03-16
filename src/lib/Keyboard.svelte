<script>
  import Key from './Key.svelte'
  export let disabledKeys = []
</script>

<div class="keyboard">
  <Key disabled={disabledKeys.includes('q')} on:key key="Q" />
  <Key disabled={disabledKeys.includes('w')} on:key key="W" />
  <Key disabled={disabledKeys.includes('e')} on:key key="E" />
  <Key disabled={disabledKeys.includes('r')} on:key key="R" />
  <Key disabled={disabledKeys.includes('t')} on:key key="T" />
  <Key disabled={disabledKeys.includes('y')} on:key key="Y" />
  <Key disabled={disabledKeys.includes('u')} on:key key="U" />
  <Key disabled={disabledKeys.includes('i')} on:key key="I" />
  <Key disabled={disabledKeys.includes('o')} on:key key="O" />
  <Key disabled={disabledKeys.includes('p')} on:key key="P" />
  <div class="space" />
  <Key disabled={disabledKeys.includes('a')} on:key key="A" />
  <Key disabled={disabledKeys.includes('s')} on:key key="S" />
  <Key disabled={disabledKeys.includes('d')} on:key key="D" />
  <Key disabled={disabledKeys.includes('f')} on:key key="F" />
  <Key disabled={disabledKeys.includes('g')} on:key key="G" />
  <Key disabled={disabledKeys.includes('h')} on:key key="H" />
  <Key disabled={disabledKeys.includes('j')} on:key key="J" />
  <Key disabled={disabledKeys.includes('k')} on:key key="K" />
  <Key disabled={disabledKeys.includes('l')} on:key key="L" />
  <div class="space" />
  <div class="spacer-key" />
  <Key disabled={disabledKeys.includes('z')} on:key key="Z" />
  <Key disabled={disabledKeys.includes('x')} on:key key="X" />
  <Key disabled={disabledKeys.includes('c')} on:key key="C" />
  <Key disabled={disabledKeys.includes('v')} on:key key="V" />
  <Key disabled={disabledKeys.includes('b')} on:key key="B" />
  <Key disabled={disabledKeys.includes('n')} on:key key="N" />
  <Key disabled={disabledKeys.includes('m')} on:key key="M" />
  <div class="spacer-key" />
</div>

<style lang="scss">
  .keyboard {
    display: grid;
    grid-template-columns: repeat(20, minmax(auto, 1.25em));
    grid-auto-rows: 3em;
    gap: 0.25em;
    justify-content: center;
  }
  .spacer-key {
    grid-column: span 3;
    visibility: hidden;
  }
</style>
