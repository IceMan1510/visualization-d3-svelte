<script>
  import ChartContainer from "./components/ChartContainer.svelte";
  import { weddings } from "./data/weddings";
</script>

<main>
  <ChartContainer
    type={"lineChart"}
    chartProps={{
      data: weddings,
      xVar: "Year",
      yVars: ["Civil", "Religious"],
    }}
  />
</main>
