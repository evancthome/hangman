<script>
  import Head from './man/Head.svelte'
  import Body from './man/Body.svelte'
  import LArm from './man/LArm.svelte'
  import RArm from './man/RArm.svelte'
  import LLeg from './man/LLeg.svelte'
  import RLeg from './man/RLeg.svelte'
  export let wrongGuesses
</script>

<div class="gallow">
  <div class="gallow-top" />
  <div class="gallow-bottom" />
  {#if wrongGuesses > 0}
    <Head />
  {/if}

  {#if wrongGuesses > 2}
    <LArm />
  {/if}
  {#if wrongGuesses > 1}
    <Body />
  {/if}
  {#if wrongGuesses > 3}
    <RArm />
  {/if}

  {#if wrongGuesses > 4}
    <LLeg />
  {/if}
  {#if wrongGuesses > 5}
    <RLeg />
  {/if}
</div>

<style>
  .gallow {
    position: absolute;
    top: 15px;
    left: 350px;
  }
  .gallow-top {
    border-top: 3px solid black;
    border-right: 3px solid black;
    width: 150px;
    height: 400px;
    position: absolute;
    top: -5px;
    left: 35px;
  }
  .gallow-bottom {
    position: absolute;
    width: 150px;
    height: 1px;
    border-bottom: 3px solid black;
    top: 395px;
    left: 105px;
  }
</style>
