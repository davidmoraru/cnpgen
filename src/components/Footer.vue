<template>
<footer class="footer has-text-centered">
  <div class="container">
    <div class="columns">
      <div class="column is-8-desktop is-offset-2-desktop">
        <div class="content" id="adsgoeshere"></div>
      </div>
    </div>
    <div class="columns">
      <div class="column is-8-desktop is-offset-2-desktop">
        <hr>
        <p>
          <a href="https://github.com/davidmoraru/cnpgen/releases/tag/0.2.0" target="_blank">
            <img class="download" src="../assets/winstorebanner-300x108.png" alt="Download for Windows 10" title="Download for Windows 10">
          </a>
          <br>
          <small>
            Se poate descarca <code>gratuit</code> de pe <a href="https://github.com/davidmoraru/cnpgen">GitHub</a>.
            <br>
            <span v-html="copy.text"></span>
          </small>

        </p>
      </div>
    </div>
  </div>
</footer>
</template>

<script>
import {
  reactive
} from 'vue'
export default {
  name: 'Footer',
  setup() {
    const copy = reactive({
      text: '&copy;' + new Date().getFullYear() + '. Cod Sursa Licentiat ca <a href="https://github.com/davidmoraru/cnpgen">MIT</a>.'
    })
    return {
      copy
    }
  }
}
</script>

<style lang="scss" scoped>
.download {
  width: 100px;
  height: auto;
}
</style>
