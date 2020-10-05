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
