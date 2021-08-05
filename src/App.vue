<template>
  <main id="app" @scroll.passive="scroll" @mousemove="mousemove">
    <section class="parrallax">
    <Parallax 
    v-for="pic in parallaxPics"
    :key="pic.title"
    :pic="pic"
    />
    <h2 id="Mtext">Moonlight</h2>
    </section>

    <Coding-is />

    <section class="products">
      <Product 
      v-for="product in products"
      :key=product.color
      :product="product"
      />
    </section>

    <section class="Pepsicard">
    <PepsiCard />
    </section>

  </main>
</template>

<script>
import CodingIs from './components/CodingIs.vue'
import PepsiCard from './components/PepsiCard.vue'
import Parallax from './components/Parallax'
import Product from './components/Product.vue'

export default {
  name: 'App',
  components: {
    Parallax,
    Product,
    CodingIs,
    PepsiCard
  },
    data() {
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
      ],
      products: [
        {
          title: 'Nike Air Max',
          color: 'green',
          bgtext: 'NIKE',
          src: require('./assets/green-shoe.png')
        },
        {
          title: 'Nike Flex',
          color: 'blue',
          bgtext: 'AIR',
          src: require('./assets/blue-shoe.png')
        },
        {
          title: 'Nike Rouche Runs',
          color: 'pink',
          bgtext: 'MAX',
          src: require('./assets/pink-shoe.png')
        }
      ]
    }
  },
  methods: {
    handleScroll() {
      let bg = document.getElementById('bg')
      let moon = document.getElementById('moon')
      let mountain = document.getElementById('mountain')
      let road = document.getElementById('road')
      let Mtext = document.getElementById('Mtext')
      // let text = document.getElementById('text')

      // console.log(this.coords(text));

      var value = window.scrollY;

      bg.style.top = value * 0.5 + 'px';
      moon.style.left = -value * 1 + 'px';
      mountain.style.top = -value * 0.15 + 'px';
      road.style.top = value * 0.15 + 'px';
      Mtext.style.top = value * 2 + 'px';

    },
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;

      let products = document.querySelectorAll('.products .product')

      for (let i=0; i<products.length; i++) {
        let product = products[i];

        let product_image = product.querySelector('.product-image-wrap');

        let img_x = mouseX - this.coords(product_image).x;
        let img_y = mouseY - this.coords(product_image).y;
        product_image.style.transform = `translateY(-${img_y/20}px) translateX(-${img_x/20}px) translateZ(100px)`;

        let bgtext = product.querySelector('.bg-text');
        let bg_x = mouseX - this.coords(bgtext).x;
        let bg_y = mouseY - this.coords(bgtext).y;

        bgtext.style.transform = `translateX(${bg_x/25}px) translateY(${bg_y/25}px)`;
      }
    },
    coords (el) {
      let coords = el.getBoundingClientRect();

      return { 
        x: coords.left / 2,
        y: coords.top /2
      }
    },
  },
  created () {
    window.addEventListener('scroll', this.handleScroll);
  }, 
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>


<style >

@import url('https://fonts.googleapis.com/css?family=Poppins:300,400,500,600,700,800,900&display=swap');
  *{
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
  }

  body {
    background: #0a2a43;
    min-height: 15000px;
  }

  .products {
    display: flex;
    flex:  3;
    flex-wrap: wrap;
    max-width: 1280px;
    padding: 25px;
    margin:  auto;
  }

  @media (max-width: 800px){
    .products{
      display: flex;
      flex: 1;
      flex-direction: column;
      margin-bottom: 20vh;
    }
  }

  .parrallax{
    position: relative;
    width: 100%;
    height: 100vh;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
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
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    pointer-events: none;
  }

  @media (max-width: 800px) {
    #moon {
      top:0;
      left:0;
      position: absolute;
      justify-content: left;
    }
  }

  #Mtext {
    position: relative;
    color: #fff;
    font-size: 10vw;
    z-index: 1;
  }
    

  #road{
    z-index: 2;
  }

  .Pepsicard{
    /* height: 400vh; */
    margin-top: 30vh;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }

</style>
