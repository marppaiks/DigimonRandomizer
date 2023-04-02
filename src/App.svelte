<script>
  import Button from './Button.svelte';
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Digimoninfo from './Digimoninfo.svelte';
  import AllDigimonList from './AllDigimonList.svelte';

  const appInfo = {
    name: 'Digimon Randomizer',
    ownName: 'Marianne Äikäs',
    year: new Date().getFullYear(),
    course: 'Frontend basics',
    // Tiedot Footerin slottiin / Header-name propsi
  };

  let showDigimonInfo = false;
  let showAllDigimonList = false;

  function showWindow() {
    showDigimonInfo = true;
  }
  function allDigimons() {
    showAllDigimonList = true;
  }
</script>

<main>
  {#if showAllDigimonList}
    <AllDigimonList on:sulje={() => (showAllDigimonList = false)} />
  {/if}
  {#if showDigimonInfo}
    <Digimoninfo on:sulje={() => (showDigimonInfo = false)} />
  {/if}
  <Header sovellus={appInfo.name} />
  <div class="start">
    <p>Interested in Digimon?</p>
    <p>
      Just press the button and get a <b>randomized</b> Digimon with their information!
    </p>
    <Button on:click={showWindow}>Get a Digimon</Button>
    <br />
    <button on:click={allDigimons}>List of all available Digimon</button>
    <br />
  </div>
</main>
<Footer>&copy; {appInfo.ownName} {appInfo.year} for {appInfo.course}</Footer>

<!-- Footer komponentille propsit-->
<style>
  b {
    -webkit-text-stroke: 0.4px #c300ff;
  }
  button {
    font-family: monospace;
    font-size: 12px;
    margin: 50px;
    padding: 15px 30px 15px 30px;
    border-radius: 50px;
    border: solid 1px black;
    background-color: #ffa200;
    color: black;
    font-family: 'Press Start 2P';
  }
  button:hover {
    background-color: black;
    color: #ffa200;
  }
  .start {
    color: #000000;
    -webkit-text-stroke: 0.6px #ffa200;
    border-radius: 100px;
    padding: 1em;
    font-size: 1.9em;
  }
  main {
    padding: 0.5em;
    text-align: center;
    background-image: url('https://freepngimg.com/thumb/digimon/30178-8-digimon-file.png');
    background-size: 35em;
    background-repeat: no-repeat;
    background-attachment: static;
    background-position: right bottom;
    margin-bottom: -30px;
  }
</style>
