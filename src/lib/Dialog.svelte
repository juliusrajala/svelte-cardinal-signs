<script lang="ts">
  export let isCorrect = false;
  export let answeredCardinal = "";
  export let showDialog = false;

  let dialog: HTMLDialogElement;

  const onOverlayClicked = (e: MouseEvent) => {
    if (e.target === dialog || dialog.contains(e.target as Node)) {
      return console.log("Dialog clicked");
    }
    return console.log("Overlay clicked");
  };
</script>

{#if showDialog}
  <div class="Overlay" on:click={onOverlayClicked}>
    <dialog bind:this={dialog} class="Answer" open>
      <header>
        <h3>You answered {answeredCardinal}</h3>
      </header>
      <div class="DialogContent">
        {#if isCorrect}
          <p>Correct!</p>
        {:else}
          <p>Incorrect!</p>
        {/if}
      </div>
      <footer>
        <button>Next sign</button>
      </footer>
    </dialog>
  </div>
{/if}

<style>
  .Overlay {
    top: 0;
    left: 0;
    z-index: 5;
    position: absolute;
    width: 100vw;
    height: 100vh;
    background: white;
    background: rgba(255, 255, 255, 0.5);
    backdrop-filter: blur(2px);
    -webkit-backdrop-filter: blur(2px);
  }

  dialog {
    position: fixed;
    top: 40vh;
    border: none;
    background-color: whitesmoke;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
    padding: 1rem 2rem;
    z-index: 10;
    border-radius: 0.5rem;
    box-sizing: border-box;
  }

  .DialogContent {
    font-weight: 600;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.5rem;
  }

  button {
    background-color: tomato;
    border: none;
    padding: 0.5rem 2rem;
    color: #fff;
    font-family: Arial, Helvetica, sans-serif;
    font-weight: 600;
    font-size: 1.3rem;
    border-radius: 0.5rem;
  }
</style>
