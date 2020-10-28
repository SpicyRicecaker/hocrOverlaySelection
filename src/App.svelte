<script lang="ts">
  import { onMount } from 'svelte';
  import { svg_element } from 'svelte/internal';
  // export let name: string;
  let canvas: HTMLCanvasElement;
  let ctx;
  // Loads all into corresponding canvas

  const imageSrc = 'seven.jpg';

  onMount(async () => {
    const image = await loadNewImage(imageSrc);
    // Load canvas stuff
    canvas = document.getElementById('canvas') as HTMLCanvasElement;
    canvas.width = image.naturalWidth;
    canvas.height = image.naturalHeight;
    ctx = canvas.getContext('2d');
    // Draw image to canvas
    // ctx.drawImage(image, 0, 0);
    ctx.drawImage(
      image,
      0,
      0,
      image.naturalWidth,
      image.naturalHeight,
      0,
      0,
      canvas.width,
      canvas.height
    );

    // ctx.fillRect(0,0,500,500);
  });
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

  body {
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
    display: flex;
    // flex-direction: column;
    overflow: auto;
    /* flex-basis: 50px; */
    /* max-height: calc(100% - 2rem); */
  }

  img {
    flex: 1;
    object-fit: contain;
  }

  canvas {
    flex: 1;
    object-fit: contain;
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
  }

  svg {
    flex: 1;
    object-fit: contain;
    // background: url('../seven.jpg');
    // display: flex;
    // flex: 1;
    // vertical-align: bottom;
    // object-fit: contain;
  }

  image {
    display: block;
    // flex: 1;
    // display: block;
    // vertical-align: bottom;
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
  <body>
    <div style="width: 100%; height: 100%">
      <div class="wrapper">
        <div class="header">HELLO WORLD</div>
        <div id="header1" class="headerType">
          <img id="img" src={imageSrc} alt="bob123" />
        </div>
        <div id="header2" class="headerType"><canvas id="canvas" /></div>
        <div id="header3" class="headerType">
          <svg
            preserveAspectRatio="xMidYMid meet"
            viewBox="0 0 1000 523"
            id="svg">
            <image width="1000" height="523" xlink:href={imageSrc} />
          </svg>
        </div>
      </div>
    </div>
  </body>
</main>
