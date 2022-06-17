<script lang="ts">
  export let options: { name: string; component: any }[] = [];
  export let setAnswer: (answer: string) => void;
</script>

{#each options as item}
  <button on:click={() => setAnswer(item.name)}>
    {item.name}
  </button>
{/each}

<style>
  button {
    width: 49%;
    border-radius: 0.5rem;
    background-color: tomato;
    padding: 1rem;
    border: none;
    font-family: Helvetica, Arial, sans-serif;
    font-weight: 600;
    font-size: 1.5rem;
    color: #fff;
    margin-bottom: 1rem;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    transition: background-color 0.1s ease-in-out;
  }

  button:hover {
    background-color: salmon;
    cursor: pointer;
  }
</style>
