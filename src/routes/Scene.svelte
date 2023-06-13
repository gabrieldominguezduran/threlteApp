<script>
  // @ts-nocheck
  import { onMount } from "svelte";
  import * as d3 from "d3";

  import Bar from "../lib/Bar.svelte";
  import Floor from "../lib/Floor.svelte";
  import Camera from "../lib/Camera.svelte";
  import Light from "../lib/Light.svelte";
  import Title from "$lib/Title.svelte";

  import MonthLabels from "../lib/MonthLabels.svelte";
  import YearLabels from "../lib/YearLabels.svelte";

  /**
   * @type {any[]}
   */
  let data = [];
  let datafiltered = [];
  let years = [];
  async function load() {
    const data_file =
      "https://raw.githubusercontent.com/stefanpullen/TutorialData/main/heathrow.csv";
    const response = await fetch(data_file);
    console.log(response);
    if (response.ok) {
      data = d3.csvParse(await response.text(), d3.autoType);
      datafiltered = data.filter((d) => d.year == 2011);
      years = [...new Set(data.map((d) => d.year))];
    }
  }
  onMount(() => {
    load();
  });

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
</script>

<Title />
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

{#each datafiltered as d}
  <MonthLabels {d} x={xScale(d.month)} y={yScale(d.rain)} z={zScale(d.year)} />
{/each}

{#each years as d, i}
  <YearLabels {d} x={9} y={0.01} z={0 + 2 * i} />
{/each}
