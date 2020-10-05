<template>
<footer class="footer">
  <small>
    <a href="https://github.com/davidmoraru/cnpgen/releases/tag/0.2.0" target="_blank">
      <img class="download" src="../assets/winstorebanner-300x108.png" alt="Download for Windows 10" title="Download for Windows 10">
    </a>
    <a href="https://github.com/davidmoraru/cnpgen" target="_blank">
      <img class="download" src="../assets/gh.png" alt="GitHub" title="GitHub">
    </a>
    <br>
    <span v-html="copy.text"></span>
  </small>
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
      text: '&copy;' + new Date().getFullYear() + '. Cod Sursă Licențiat ca <a>MIT</a>.'
    })
    return {
      copy
    }
  }
}
</script>

<style lang="scss" scoped>
.download {
  height: 20px;
  width: auto;
}

.footer {
  max-height: 100px;
  background-color: #001a42;
  border: 1px solid #001a42;
  border-top: 2px solid #000c1d;
}

.footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  color: white;
  text-align: center;
  padding: 1rem 1rem 1rem;
}
</style>
