<script>
  import { createEventDispatcher } from 'svelte'
  export let key
  export let disabled = false

  const dispatch = createEventDispatcher()

  const dispatchKey = () => {
    dispatch('key', { key: { key } })
  }
</script>

<button {disabled} on:click={dispatchKey} class="key" data-key={key}
  >{key}</button
>

<style>
  .key {
    font-size: clamp(0.5rem, 2.5vmin, 1.5rem);
    padding: 1em;
    grid-column: span 2;
    border: none;
    border-radius: 0.25em;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    user-select: none;
    font-family: monospace;
    font-weight: bold;
    transition: background-color 100ms ease-in-out;
  }
</style>
