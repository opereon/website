<template>
  <div class="flex flex-col items-center md:mx-2 w-full px-4 py-8 mb-4 text-center md:flex-1 feature-main">
    <svg class="feature-background">
      <rect x="0" y="0" width="100%" height="100%" style="stroke: none; fill: url(#hexagons);"/>
      <defs>
        <pattern id="hexagons" x="0" y="12" width="28" height="49" patternUnits="userSpaceOnUse">
          <path fill="var(--color-ui-secondary)" d="M13.99 9.25l13 7.5v15l-13 7.5L1 31.75v-15l12.99-7.5zM3 17.9v12.7l10.99 6.34 11-6.35V17.9l-11-6.34L3 17.9zM0 15l12.98-7.5V0h-2v6.35L0 12.69v2.3zm0 18.5L12.98 41v8h-2v-6.85L0 35.81v-2.3zM15 0v7.5L27.99 15H28v-2.31h-.01L17 6.35V0h-2zm0 49v-8l12.99-7.5H28v2.31h-.01L17 42.15V49h-2z"/>
        </pattern>
      </defs>
    </svg>
    <font-awesome :icon="[icon_style, icon]" size="3x" class="mb-6 text-ui-primary"></font-awesome>
    <h3 class="font-bold tracking-wide uppercase text-ui-primary">
      {{title}}
    </h3>
    <p class="text-lg text-center">
      {{desc}}
    </p>
  </div>
</template>

<script>
  export default {
    name: "FeatureTile",
    props: ['title', 'desc', 'icon', 'icon_style']
  }
</script>

<style lang="scss">
  .feature-main {
    position: relative;
    z-index: 1;
    svg.feature-background {
      position: absolute;
      top: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      border: 1px solid var(--color-ui-secondary);
    }
  }
</style>
