<script>
  import { fade, fly, slide } from 'svelte/transition';
</script>

<button in:slide={{ duration: 1000, x: 300, y: 0 }} out:fade on:click
  ><slot /></button
>

<style>
  button {
    font-family: monospace;
    font-size: 1.3em;
    padding: 15px 30px 15px 30px;
    border: 4px dashed #ffa200;
    border-radius: 50px;
    background-color: #000000;
    color: #ffa200;
    font-family: 'Press Start 2P';
    margin-top: 20px;
  }
  button:hover {
    background-color: #ffa200;
    color: black;
    border: 4px dashed rgb(0, 0, 0);
  }
  @media (min-width: 340px) {
    button {
      font-size: 1em;
    }
  }
</style>
