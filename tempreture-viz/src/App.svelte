<script>
  import * as d3 from "d3";
  import Header from "./components/Header.svelte";
  import LineChart from "./components/LineChart.svelte";

  let lineChartData;

  d3.csv("../data/temperatures.csv").then((data) => (lineChartData = data));
</script>

<main>
  <div class="app">
    <Header />
    {#if lineChartData}
      <LineChart data={lineChartData} />
      <LineChart data={lineChartData} />
    {/if}
  </div>
</main>

<style>
  .app {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 100%;
    width: 100%;
    user-select: none;
  }
</style>
