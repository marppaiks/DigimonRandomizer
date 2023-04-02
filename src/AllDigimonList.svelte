<script>
  //Komponentti, joka antaa kaikki Digimonit API:sta fetchillä listana
  import { fade, fly } from 'svelte/transition';
  import { onMount } from 'svelte';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  export let close = 'Close';
  export let digimonit = [];

  import Modal from './Modal.svelte';
  import Button from './Button.svelte';
  let name = 'List of all Digimon';

  function sulje() {
    dispatch('sulje'); //Nappi sulkee modaalin
  }

  onMount(async () => {
    //Hakii kaikki digimannit taulukkoon objekteina (Heti kun sovellus käynnistyy)
    const response = await fetch('https://digimon-api.vercel.app/api/digimon');
    if (!response.ok) {
      throw new Error('Cannot fetch data.');
    }
    digimonit = await response.json();
    console.log(digimonit);
  });
</script>

<Modal>
  <div class="ulkobutton">
    <Button on:click={sulje}>{close}</Button>
  </div>
  <div slot="header"><h1>{name}</h1></div>

  {#each digimonit as digimon}
    <!-- Jokainen nimi kerrallaan tulostetaan (suoritetaan vasta kun promise fullfilled) -->
    <div class="lista">
      <p in:fly={{ duration: 2000, x: 0, y: 200 }} out:fade>
        {digimon.name}
      </p>
    </div>

    <!--Kutsutaan taulukosta objektia kerrallaan-->
  {/each}
</Modal>

<style>
  .lista {
    display: flex;
    justify-content: center;
  }
  .ulkobutton {
    position: fixed;
    top: 4vh;
    right: 12vw;
  }
  p {
    padding: 10px 20px 10px 20px;
    border-radius: 200px;
    padding-bottom: 10px;
    font-size: 20px;
    -webkit-text-stroke: 0.6px #3300ff;
    background-color: rgba(255, 184, 78, 0.558);
  }
  h1 {
    padding-top: 20px;
  }
</style>
