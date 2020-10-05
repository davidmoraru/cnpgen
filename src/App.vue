<template>
<section class="section" id="content-wrap">
  <Header />
  <Gen />
</section>
<Footer />
</template>

<script>
import Header from './components/Header.vue'
import Gen from './components/Gen.vue'
import Footer from './components/Footer.vue'
export default {
  name: 'App',
  components: {
    Gen,
    Footer,
    Header
  }
}
</script>

<style lang="scss">
* {
  scrollbar-width: thin;
  scrollbar-color: #001a42 #ffffff;
}

*::-webkit-scrollbar {
  display: none;
  width: 10px;
}

*::-webkit-scrollbar-track {
  background: rgb(255, 255, 255);
}

*::-webkit-scrollbar-thumb {
  background-color: #001a42;
  border-radius: 20px;
  border: 3px solid rgb(255, 255, 255);
}

body {
  position: relative;
}

section {
  padding: 0 !important;
}

section {
  padding-top: 1rem !important;
}

#app {
  position: relative;
  min-height: 90vh;
}

body::after {
  content: '';
  display: block;
  height: 50px;
  /* Set same as footer's height */
}

#content-wrap {
  padding-bottom: 3rem;
}

.input,
.textarea,
.select select {
  border-radius: 0px !important;
}
</style>
