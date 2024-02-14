<script>
  import {onMount} from 'svelte'
  // from http://inertia-momentum-scroll.webflow.io/vanilla-js-version 
// CJHersh https://webflow.com/CJHersh

// First we get the elements we need, the body and our container on which
// we are going to apply a smooth scroll. You will always need a container
// to apply a smooth scroll. You will not be able to apply it directly to
// the body.
let body
let main
let windowVar

// We define variables we will need later. 
// 2 variables to store the scroll position and 2 variables to store the 
// container position.
let sx = 0;
let sy = 0;

let dx = sx;
let dy = sy;

// The trick is to set a height to the body to keep the browser scroll bar.
// body.style.height = main.clientHeight + 'px';

// Then we fix our container so it won't move when the user scrolls.
// We will move it ourself with the Linear Interpolation and translations.


// We bind a scroll event to the window to watch scroll position.

function scroll() {
  // We only update the scroll position variables
  //sx = windowVar.pageXOffset;
  //sy = window.pageYOffset;
  console.log(dx, dy)
}

function getXOffset() {

}

function getYOffset() {

}


function render() {
  // We calculate our container position by using our Linear Interpolation method.

  // And we loop again.

  dx = lerp(dx, sx, 0.05);
  dy = lerp(dy, sy, 0.05);
  
  dx = Math.floor(dx * 100) / 100;
  dy = Math.floor(dy * 100) / 100;

  //main.style = `translate: (-${dx}px, -${dy}px;`
  //console.log(main.style)
  requestAnimationFrame(render);
}

// This is our Linear Interpolation method.
function lerp(a, b, n) {
  return (1 - n) * a + n * b;
}

  onMount(() => {
    requestAnimationFrame(render);
  })
</script>


<svelte:window on:scroll={scroll} bind:scrollY={sy} bind:scrollX={sx} />

<body>

  <main bind:this={main} style='transform: translate(-{dx}px, -{dy}px)'>
    <section class="section">
      <strong>1</strong>
    </section>
    <section class="section">
      <strong>2</strong>
    </section>
    <section class="section">
      <strong>3</strong>
    </section>
    <section class="section">
      <strong>4</strong>
    </section>
    <section class="section">
      <strong>5</strong>
    </section>
  </main>
</body>


<style>
  html, body {
  margin: 0; padding: 0;
}

main {
  width: 100%;
}

.section {
  box-sizing: border-box;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: sans-serif;
  font-size: 4em;
  &:first-child {
    background-color: #ccc;
  }
  &:nth-child(2) {
    color: #efefef;
    background-color: #212121;
  }
  &:nth-child(3) {
    background-color: #888;
  }
  &:nth-child(4) {
    background-color: #f00;
  }
}

.all {
  width: 100vw;
  height: 100vh;
  z-index: 0;
  position:sticky;
  top:0;
}
</style>