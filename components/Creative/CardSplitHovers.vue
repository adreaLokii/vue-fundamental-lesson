<template>
  <main id="main" class="w-3/4">
    <h1 class="text-4xl text-center mb-8">Card Split Hovers</h1>
    <div class="flex justify-around text-white">
      <div class="card">
        <img
            src="https://images.unsplash.com/photo-1535498730771-e735b998cd64?ixlib=rb-1.2.1&amp;ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&amp;auto=format&amp;fit=crop&amp;w=687&amp;q=80"
            alt="A City skyline at sunset"/>
        <div class="text ">
          <h2 data-splitting="">The City</h2>
          <p data-splitting="">Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos excepturi nostrum
            necessitatibus
            doloremque? Quasi non molestias odio. Quasi non molestias odio.
          </p>
        </div>
      </div>
      <div class="card">
        <img
            src="https://images.unsplash.com/photo-1586500036706-41963de24d8b?ixlib=rb-1.2.1&amp;ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&amp;auto=format&amp;fit=crop&amp;w=687&amp;q=80"
            alt="A City skyline at sunset"/>
        <div class="text">
          <h2 data-splitting="">The Beach</h2>
          <p data-splitting=""> Quasi non molestias odio. Lorem ipsum dolor sit amet consectetur adipisicing elit.
            Dignissimos excepturi
            nostrum necessitatibus doloremque? Quasi non molestias odio.
          </p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "CardSplitHovers"
}
</script>

<style lang="scss">
:root {
  --cover-timing: 0.5s;
  --cover-ease: cubic-bezier(0.66, 0.08, 0.19, 0.97);
  --cover-stagger: 0.15s;

  --text-timing: .75s;
  --text-stagger: 0.015s;
  --text-ease: cubic-bezier(0.38, 0.26, 0.05, 1.07);

  --title-stagger: 0.05s;
  --highlight: white;
}


.card {
  position: relative;
  overflow: hidden;
  aspect-ratio: 9/12;
  display: flex;
  flex-direction: column;
  border-radius: 7px;
  box-shadow: rgba(255, 255, 255, 0.3) 0 5vw 6vw -8vw,
  rgba(255, 255, 255, 0) 0 4.5vw 5vw -6vw,
  rgba(50, 50, 80, 0.5) 0px 4vw 8vw -2vw,
  rgba(0, 0, 0, 0.8) 0px 4vw 5vw -3vw;

  transition: box-shadow 1s var(--cover-ease);

& > * {
    z-index: 2;
  }

& > img {
    z-index: 0;
    transition: all .8s cubic-bezier(0.66, 0.08, 0.19, 0.97);;
  }

&::before,
&::after {
   content: "";
   width: 100%;
   height: 50%;
   top: 0;
   left: 0;
   background: rgba(0, 0, 0, 0.5);
   position: absolute;
   transform-origin: left;
   transform: scaleX(0);
   transition: all var(--cover-timing) var(--cover-ease);
   z-index: 1;
 }

&::after {
   transition-delay: var(--cover-stagger);
   top: 50%;
 }

&:hover {
   box-shadow: white 0 5vw 6vw -9vw,
   var(--highlight) 0 5.5vw 5vw -7.5vw,
   rgba(50, 50, 80, 0.5) 0px 4vw 8vw -2vw,
   rgba(0, 0, 0, 0.8) 0px 4vw 5vw -3vw;

&::before,
&::after {
   transform: scaleX(1);
 }

& h2 .char,
& p .word {
    opacity: 1;
    transform: translateY(0);
    color: inherit;
  }

& h2 .char {
    transition-delay: calc(0.1s + var(--char-index) * var(--title-stagger));
  }

& p .word {
    transition-delay: calc(0.1s + var(--word-index) * var(--text-stagger));
  }

& img {
    transform: scale(1.1);
  }

}

&:nth-of-type(1) {
   --highlight: coral;
 }

&:nth-of-type(2) {
   --highlight: #56ffe5;
 }

}

.text {
  position: absolute;
  inset: 20px;
  top: auto;
}

h2 {
  font-size: 30px;
  font-size: clamp(20px, 4vw, 40px);
  font-weight: 800;
  margin-bottom: 0.2em;
}

p {
  font-size: 12px;
  font-size: clamp(10px, 1.25vw, 14px);
  line-height: 1.4;
  text-align: justify;
  margin-top: 0.2em;
  margin-bottom: 0;
}

h2 .char,
p .word {
  color: var(--highlight);
  display: inline-block;
  opacity: 0;
  position: relative;
  transform: translateY(20px);
  transition-property: transform, opacity, color;
  transition-timing-function: var(--text-ease);
  transition-duration: var(--text-timing), var(--text-timing), calc(var(--text-timing) * 2);
}

img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 7px;
}


// layout stuff

   main {
     grid-template-columns: 1fr;
     grid-template-rows: 60px;
     grid-gap: 2em;
@media screen and (min-width: 600px) {
  grid-template-columns: 1fr 1fr;
  grid-template-rows: min-content 1fr;
}
}

.card {
  width: 90vw;
  max-width: 300px;
@media screen and (min-width: 600px) {
  width: 40vw;
}
}

h1 {
  font-weight: 100;
@media screen and (min-width: 600px) {
  grid-column: 1/3;
}
}

body, html {
  padding: 0;
  margin: 0;
  min-height: 100vh;
  font-family: "Open Sans", sans-serif;

}
</style>