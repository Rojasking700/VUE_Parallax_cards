<template>
  <main id="app">
    <section>
    <Parallax 
    v-for="pic in parallaxPics"
    :key="pic.title"
    :pic="pic"
    />
    </section>
  </main>
</template>

<script>

import Parallax from './components/Parallax.vue'

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
  }
}
</script>

<style>

</style>
