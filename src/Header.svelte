<script>
  export let sovellus = 'xxx'; //Tulee app.infosta
</script>

<header>
  <h1>{sovellus.toUpperCase()}</h1>
  <!--propsitulostus-->
</header>

<style>
  header {
    background-image: linear-gradient(to bottom, #0400771a, #ffa20066),
      url('https://media2.giphy.com/media/xULW8l2gXuRPmsQe8U/giphy.gif');
    color: rgb(255, 162, 0);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 5em;
    margin-top: 35px;
    padding: 40px;
    border-radius: 50px;
    letter-spacing: 0.3em;
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.5);
    -webkit-text-stroke: 2.5px rgb(4, 0, 119);
  }
</style>
