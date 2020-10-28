<script lang="ts">
  interface boundingBox {
    x0: number;
    y0: number;
    x1: number;
    y1: number;
  }

  interface boundingBoxes extends Array<boundingBox> {}
  export let boundingBoxes: boundingBoxes = [];
</script>

<style lang="scss">
</style>

{#each boundingBoxes as bbox}
  <rect
    x={bbox.x0}
    y={bbox.y0}
    width={bbox.x1 - bbox.x0}
    height={bbox.y1 - bbox.y0} />
{/each}
