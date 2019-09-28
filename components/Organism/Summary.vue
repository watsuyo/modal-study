<template>
  <div>
    <Header />
    <template v-if="isBackdrop">
      <div class="overlay">
        <Backdrop @backdrop="backdrop" />
      </div>
    </template>
    <button class="backdropButton" @click="backdrop">Backdrop</button>
    <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Backdrop from '../Atom/Backdrop'
import Header from '../Atom/Header'
import Footer from '../Atom/Footer'

export default Vue.extend({
  components: {
    Backdrop,
    Header,
    Footer
  },
  data() {
    return {
      isBackdrop: false
    }
  },
  methods: {
    backdrop() {
      this.isBackdrop = this.isBackdrop !== true
    }
  }
})
</script>

<style scoped>
.backdropButton {
  position: absolute;
  top: 100px;
  left: 150px;
  width: 100px;
}
.overlay {
  position: fixed;
  z-index: 1;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>