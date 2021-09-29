<template>
  <Nav />
  <Hero />
  <About />
</template>

<script>
  import Nav from "./components/Nav.vue"
  import Hero from "./components/Hero.vue"
  import About from "./components/About.vue"
  export default {
    name: 'App',
    components: {
      Nav,
      Hero,
      About
    },
    setup() {
        return {
        }
    },
  }
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Spartan:wght@500;600;700&display=swap');
  html , body , #app {
    width: 100%;
    height: 100vh;
  }
  html { 
    min-width: 320px; 
    background: white;
    font-size: 12px;
  }
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Spartan', sans-serif;
  }
  a {
    text-decoration: none;
  }
  #app {
    position: relative;
    overflow-x: hidden;

  } 
</style>
