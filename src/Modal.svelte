<script>
</script>

<div class="scroller">
  <div class="backdrop" />

  <div class="modal">
    <header>
      <slot name="header" />
    </header>
    <slot />
    <br />
    <footer>
      <slot name="footer" />
    </footer>
  </div>
</div>

<style>
  .scroller {
    scrollbar-color: #040077 rgb(0, 0, 0);
    scrollbar-width: thin;
    border-radius: 20px;
  }
  header {
    margin: 0;
    padding-bottom: 2em;
    text-transform: uppercase;
    color: #ffa200;
    letter-spacing: 0.4em;
    -webkit-text-stroke: 1px #040077;
  }

  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(8, 21, 135, 0.5);
    z-index: 10;
  }

  .modal {
    padding: 1rem;
    position: fixed;
    top: 10vh;
    left: -1.5vw;
    width: 100%;
    max-height: 75vh;
    overflow: hidden;
    background-color: #ffa200; /* For browsers that do not support gradients */
    background-image: linear-gradient(#0a133b, #ffa20084),
      url('https://media2.giphy.com/media/xULW8l2gXuRPmsQe8U/giphy.gif');
    border: solid 2px black;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow-y: scroll;
  }
</style>
