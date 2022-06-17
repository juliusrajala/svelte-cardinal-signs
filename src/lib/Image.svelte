<script lang="ts">
  import logo from "../assets/svelte.png";

  export let imageData: Image = {
    src: logo,
    altText: "An outlined red letter S",
    title: "Svelte",
  };
</script>

<div>
  <img alt={imageData.altText} src={imageData.src} />
</div>

<style>
</style>
