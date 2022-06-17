<script lang="ts">
  import Dialog from "./lib/Dialog.svelte";
  import East from "./lib/cardinals/East.svelte";
  import North from "./lib/cardinals/North.svelte";
  import South from "./lib/cardinals/South.svelte";
  import West from "./lib/cardinals/West.svelte";
  import AnswerOptions from "./lib/AnswerOptions.svelte";

  const queue = [
    {
      name: "East",
      component: East,
    },
    {
      name: "North",
      component: North,
    },
    {
      name: "South",
      component: South,
    },
    {
      name: "West",
      component: West,
    },
  ];

  // selected is random item from queue
  let cardinalToQuess = queue[Math.floor(Math.random() * queue.length)];
  let answeredCardinal = "";
  $: showDialog = answeredCardinal !== "";
  $: isCorrect = answeredCardinal === cardinalToQuess.name;
</script>

<main>
  <section class="SelectedQuestion">
    <svelte:component this={cardinalToQuess.component} />
  </section>
  <section class="AnswerOptions">
    <AnswerOptions
      options={queue}
      setAnswer={(clicked) => (answeredCardinal = clicked)}
    />
  </section>
</main>
<Dialog bind:showDialog bind:answeredCardinal bind:isCorrect />

<style>
  :root {
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  }

  main {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    padding: 1em;
    margin: 0;
    width: 100vw;
    justify-content: center;
    align-items: center;
  }

  section {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-width: 500px;
    padding: 2rem;
  }

  .SelectedQuestion {
    border-radius: 1rem;
    background-image: linear-gradient(
      125deg,
      hsl(207deg 75% 42%) 0%,
      hsl(207deg 74% 43%) 32%,
      hsl(206deg 72% 44%) 52%,
      hsl(202deg 69% 49%) 71%,
      hsl(199deg 74% 56%) 100%
    );
  }

  .AnswerOptions {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 1rem 0rem;
  }

  @media (min-width: 480px) {
  }
</style>
