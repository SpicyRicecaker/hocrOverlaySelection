<script lang="ts">
  import Rect from './Rect.svelte';
  // export let name: string;
  // let canvas: HTMLCanvasElement;
  // let ctx;
  // Loads all into corresponding canvas

  const imageSrc = 'fiveplus.png';
  let imageArray: HTMLImageElement[] = [];
  
  // interface boundingBox = {}

  const boundingBoxes = [
    { x0: 0, y0: 0, x1: 500, y1: 250 },
    { x0: 800, y0: 800, x1: 1600, y1: 1800 },
    { x0: 2000, y0: 1500, x1: 3000, y1: 200 },
    { x0: 1357, y0: 230, x1: 2000, y1: 500 },
    { x0: 250, y0: 314, x1: 1000, y1: 600 },
  ];

  const addImage = async () => {
    imageArray = [...imageArray, await loadNewImage(imageSrc)];
  };

  // const image = await loadNewImage(imageSrc);
  // imageArray.push(image);
  // Load canvas stuff
  // canvas = document.getElementById('canvas') as HTMLCanvasElement;
  // canvas.width = image.naturalWidth;
  // canvas.height = image.naturalHeight;
  // ctx = canvas.getContext('2d');
  // Draw image to canvas
  // ctx.drawImage(image, 0, 0);
  // ctx.drawImage(
  //   image,
  //   0,
  //   0,
  //   image.naturalWidth,
  //   image.naturalHeight,
  //   0,
  //   0,
  //   canvas.width,
  //   canvas.height
  // );
  // ctx.fillRect(0,0,500,500);
  // Loads new image
  const loadNewImage = (src: string): Promise<HTMLImageElement> =>
    new Promise((resolve) => {
      const image = new Image();
      image.onload = () => resolve(image);
      image.src = src;
    });
</script>

<style lang="scss">
  :global(body) {
    padding: 0;
    margin: 0;
  }

  main {
    max-width: 100vw;
    max-height: 100vh;
    width: 100vw;
    height: 100vh;
  }

  .wrapper {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
  }

  .header {
    font-family: 'Bebas Neue', cursive;
    font-size: 2rem;
    padding: 1rem;
    background-color: white;
    position: sticky;
    box-shadow: 0rem 0.2rem 0.4rem 0.2rem #efefef;
  }

  .headerType {
    background-color: aliceblue;
    flex: 1;
    // display: flex;
    // flex-direction: column;
    overflow: auto;
    /* flex-basis: 50px; */
    /* max-height: calc(100% - 2rem); */
  }

  // img {
  //   flex: 1;
  //   object-fit: contain;
  // }

  // canvas {
  //   flex: 1;
  //   object-fit: contain;
  /* display: block; */
  /* flex: 0 0 100%; */
  // vertical-align: bottom;
  /* width: 100%; */
  /* height: 0; */
  /* max-width: 100%;
    max-height: 100% */
  /* width: 100%;
    height: 100%; */
  /* max-width: 100%;
    max-height: 100%; */
  /* object-fit: cover; */
  /* width: 100vw;
    height: 100vh; */
  /* align-self: center; */
  // }

  svg {
    // flex: 1;
    // object-fit: contain;
    // background: url('../seven.jpg');
    // display: flex;
    // flex: 1;
    // vertical-align: bottom;
    // object-fit: contain;
  }

  image {
    // display: block;
    // flex: 1;
    // display: block;
    vertical-align: bottom;
    // object-fit: contain;
    // flex: 1;
    // display: block;
    /* flex: 0 0 100%; */
    // vertical-align: bottom;
    /* width: 100%; */
    // object-fit: contain;
  }
  /* main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  } */
</style>

<svelte:head>
  <link
    href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap"
    rel="stylesheet" />
</svelte:head>

<main>
  <div class="wrapper">
    <div class="header">
      HELLO WORLD
      <button on:click={addImage}>ADD NEW IMAGE BOI</button>
    </div>
    {#each imageArray as image}
      <div class="headerType">
        <svg viewBox="0 0 {image.naturalWidth} {image.naturalHeight}">
          <image
            width={image.naturalWidth}
            height={image.naturalHeight}
            xlink:href={image.src} />
          <!-- <Rect {boundingBoxes} /> -->
        </svg>
      </div>
    {/each}
  </div>
</main>
