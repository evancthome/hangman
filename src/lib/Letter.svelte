<script>
  export let letter
  export let show = false
</script>

<div class="letter">
  {#if show}
    {letter}
  {/if}
</div>

<style>
  .letter {
    font-size: 2rem;
    padding: 0.125rem;
    width: 1.25ch;
    border-bottom: 3px solid black;
    user-select: none;
    text-align: center;
  }
</style>
