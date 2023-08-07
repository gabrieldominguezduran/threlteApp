<script>
  import { Canvas } from "@threlte/core";
  import Scene from "./Scene.svelte";
  let selectedYear = "all";
</script>

<div class="radio-inputs">
  <label>
    <input type="radio" bind:group={selectedYear} value={2010} />
    2010
  </label>
  <label>
    <input type="radio" bind:group={selectedYear} value={2011} />
    2011
  </label>
  <label>
    <input type="radio" bind:group={selectedYear} value={2012} />
    2012
  </label>
  <label>
    <input type="radio" bind:group={selectedYear} value="all" />
    All
  </label>
</div>

<div class="canvas-wrapper">
  <Canvas>
    <Scene {selectedYear} />
  </Canvas>
</div>

<style>
  .canvas-wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
  }

  .radio-inputs {
    margin: 0 auto;
    padding: 1rem;
    z-index: 1;
  }
</style>
