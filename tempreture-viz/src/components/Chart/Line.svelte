<script>
  import * as d3 from "d3";

  export let data;
  export let xAccessor;
  export let yAccessor;

  const interpolation = d3.curveMonotoneX;

  $: lineGenerator = d3.line().x(xAccessor).y(yAccessor).curve(interpolation);

  $: line = lineGenerator(data);
</script>

<path class="line" d={line} />

<style>
  .line {
    fill: none;
    stroke: #ff0000;
    stroke-width: 3px;
    stroke-linecap: round;
  }
</style>
