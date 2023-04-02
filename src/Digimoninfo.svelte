<script>
  // Komponentti, joka tulostaa yhden Digimonin tiedot
  import { fade, fly } from 'svelte/transition';
  import { onMount } from 'svelte';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  // Custom eventti import on: -direktiiviin

  export let close = 'Close';

  import Modal from './Modal.svelte';
  import Button from './Button.svelte';

  function sulje() {
    dispatch('sulje');
  }

  const endpointApi = 'https://digimon-api.vercel.app/api/digimon'; //Alustavasti määritetly endpointti
  const getDigimon = async () => {
    const response = await fetch(endpointApi);
    if (!response.ok) {
      throw new Error('Cannot fetch data.');
    }
    let data = await response.json();

    let arvottuLuku = Math.floor(Math.random() * (data.length - 1) + 1);
    return data[arvottuLuku]; //Hakee YHDEN RANDOMIN (palautettu promisen arvo)
  };

  onMount(async () => {
    //Hakee digimonin kun appi käynnistyy
    getDigimon();
  });
</script>

<Modal>
  <div class="ulkobutton">
    <Button on:click={sulje}>{close}</Button>
  </div>
  {#await getDigimon()}
    <div class="centeri"><p>...waiting</p></div>
    <!-- Tämä näkyy niin kauan, kunnes haku on valmis-->
  {:then digimon}
    <!-- Promise fullfilled: tulokset -->
    <h1>{digimon.name}</h1>
    <img
      in:fly={{ duration: 2500, x: 0, y: -300 }}
      out:fade
      src={digimon.img}
      alt="digimon"
    />
    <div class="centeri"><p>Level: {digimon.level}</p></div>
  {:catch error}
    <!-- Jos haku ei onnistu -->
    <div class="centeri"><p>An error occurred!</p></div>
  {/await}
</Modal>

<style>
  .centeri {
    display: flex;
    justify-content: center;
  }
  .ulkobutton {
    position: fixed;
    top: 4vh;
    right: 12vw;
  }
  h1 {
    font-size: 25px;
    letter-spacing: 5px;
    -webkit-text-stroke: 0.6px #ffa200;
    margin-bottom: 1em;
  }
  p {
    color: black;
    -webkit-text-stroke: 0.6px #3300ff;
    font-size: 15px;
    margin-top: 10px;
    background-color: rgba(255, 184, 78, 0.773);
    border-radius: 200px;
    padding: 10px;
    max-width: 50%;
  }
  img {
    width: 300px;
    border: 1px solid black;
    border-radius: 50%;
  }
</style>
