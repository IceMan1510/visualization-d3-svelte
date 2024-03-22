<script>
  import { scaleBand, scaleLinear } from "d3-scale";
  const data = [
    { x: "January", value: 10000 },
    { x: "February", value: 12000 },
    { x: "March", value: 18000 },
    { x: "April", value: 11000 },
    { x: "May", value: 9000 },
  ];

  const width = 800;
  const height = 600;

  const margin = { top: 20, right: 20, bottom: 20, left: 180 };
  const innerHeight = height - margin.top - margin.bottom;
  const innerWidth = width - margin.left - margin.right;

  $: xDomain = data.map((d) => d.x);
  $: yDomain = data.map((d) => +d.value);
  $: yScale = scaleBand().domain(yDomain).range([0, innerHeight]).padding(0.1);
  $: xScale = scaleLinear()
    .domain([0, Math.max.apply(null, yDomain)])
    .range([0, innerWidth]);
  console.log(yScale);
  let yPath = `M-6,${height + 0.5}H0.5V0.5H-6`;
</script>

<svg {width} {height}>
  <g transform={`translate(${margin.left},0)`}>
    <path stroke="black" d={yPath} fill="none" />
    {#each yScale as y}
      <g class="tick" opacity="1" transform="translate(0,{xScale(y)}})">
        <line stroke="currentColor" x2="-5" />
        <text dy="0.32em" fill="currentColor" x="-{margin.left}">
          {y}
        </text>
      </g>
    {/each}
  </g>
</svg>
