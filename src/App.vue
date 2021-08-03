<template>
  <main id="app" @scroll.passive="scroll">
    <section class="parrallax">
    <Parallax 
    v-for="pic in parallaxPics"
    :key="pic.title"
    :pic="pic"
    />
    <h2 id="Mtext">Moonlight</h2>
    </section>
  </main>
</template>

<script>

import Parallax from './components/Parallax'

export default {
  name: 'App',
  components: {
    Parallax
  },
  data () {
    return {
      parallaxPics: [
        {
          title: 'bg',
          src: require('./assets/bg.jpg')
        },
        {
          title: 'moon',
          src: require('./assets/moon.png')
        },
        {
          title: 'mountain',
          src: require('./assets/mountain.png')
        },
        {
          title: 'road',
          src: require('./assets/road.png')
        },
      ]
    }
  },
  methods: {
    handleScroll() {
      console.log("scrolling")
      let bg = document.getElementById('bg')
      let moon = document.getElementById('moon')
      let mountain = document.getElementById('mountain')
      let road = document.getElementById('road')
      let Mtext = document.getElementById('Mtext')

      var value = window.scrollY;

      bg.style.top = value * 0.5 + 'px';
      moon.style.left = -value * 1 + 'px';
      mountain.style.top = -value * 0.15 + 'px';
      road.style.top = value * 0.15 + 'px';
      Mtext.style.top = value * 1 + 'px';
    }
  },
  created () {
  window.addEventListener('scroll', this.handleScroll);
}, 
destroyed () {
  window.removeEventListener('scroll', this.handleScroll);
}
}
</script>


<style>
*{
        margin: 0;
        padding: 0;
    }

    body {
        background: #0a2a43;
        min-height: 15000px;
    }

    .parrallax{
        position: relative;
        width: 100%;
        height: 100vh;
        overflow: hidden;
        display: flex;
        justify-content: center;
        align-content: center;
    }

    
    .parrallax:before{
      content: '';
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 100px;
      background: linear-gradient(to top, #0a2a43, transparent);
      z-index: 1000;
    }

    .parrallax:after{
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background:#0a2a43;
      z-index: 1000;
      mix-blend-mode: color;
    }

      .parrallax img{
          position: absolute;
          top:0;
          left:0;
          width: 100%;
          height: 100%;
          object-fit: cover;
          pointer-events: none;
      }

    #Mtext {
        position: relative;
        color: #fff;
        font-size: 10em;
        z-index: 1;
    }

    #road{
        z-index: 2;
    }
</style>
