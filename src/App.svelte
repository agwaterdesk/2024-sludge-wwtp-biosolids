<script>
  import Window from "./components/Window.svelte";
  import Map from "./components/Map.svelte";

  // Handle responsive iframes for embeds
  import pym from "pym.js";

  new pym.Child({
    polling: 500,
  });

  function getUrlParameter(name) {
    const params = new URLSearchParams(window.location.search);
    return params.get(name);
  }

  let includeCredit = getUrlParameter("credit") != "false";
</script>

<Window />
<!-- Outer div must have class 'chart-container' don't change -->
<div class="chart-container">
  <h1 class="headline">
    Most sewage sludge from wastewater treatment plants is applied to land
  </h1>
  <p class="dek">
    More than half of all sewage sludge, sometimes called biosolids, generated
    at wastewater treatment plants is spread on land as fertilizer. Most of the
    rest is buried in landfills or burned in incinerators. While it provides
    soil with nutrients, sludge can also pose environmental risks, including
    PFAS contamination. The U.S. Environmental Protection Agency collects annual
    reports from roughly 2,500 larger facilities that generate sewage sludge.
    For more information on the facilities and states included in the EPA's ECHO
    database, please visit the
    <a
      target="_blank"
      href="https://www.epa.gov/biosolids/basic-information-about-biosolids#basics"
      >EPA's website</a
    >.
  </p>
  <p class="sr-only">[altText]</p>

  <Map />

  {#if includeCredit}
    <div class="credit">
      Data: <a target="_blank" href="https://www.epa.gov/biosolids">EPA</a
      >; Graphic by Jared Whalen /
      <a target="_blank" href="https://agwaterdesk.org/">Ag & Water Desk</a>
    </div>
  {/if}
</div>

<style lang="scss">
  .chart-container {
    max-width: 800px;
    width: 100%;
    padding: 1rem;
  }
</style>
