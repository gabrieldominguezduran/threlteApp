<script>
  // @ts-nocheck

  import { T } from "@threlte/core";
  import { onMount } from "svelte";
  import * as d3 from "d3";

  import Bar from "../lib/Bar.svelte";
  import Floor from "../lib/Floor.svelte";
  import Camera from "../lib/Camera.svelte";
  import Light from "../lib/Light.svelte";

  /**
   * @type {any[]}
   */
  let data = [];

  async function load() {
    const data_file =
      "https://raw.githubusercontent.com/stefanpullen/TutorialData/main/heathrow.csv";
    const response = await fetch(data_file);
    console.log(response);
    if (response.ok) {
      data = d3.csvParse(await response.text(), d3.autoType);
    }
  }
  $: xScale = d3
    .scaleBand()
    .domain(data.map((d) => d.month))
    .range([-10, 10]);

  $: yScale = d3
    .scaleLinear()
    .domain(d3.extent(data.map((d) => d.rain)))
    .range([0, 5]);

  $: zScale = d3
    .scaleLinear()
    .domain(d3.extent(data.map((d) => d.year)))
    .range([0, 4]);

  onMount(() => {
    load();
  });
</script>

<Floor />
<Camera />
<Light />

{#each data as d}
  <Bar
    x={xScale(d.month)}
    y={yScale(d.rain)}
    z={zScale(d.year)}
    color={"#B392AC"}
    castShadow
  />
{/each}
