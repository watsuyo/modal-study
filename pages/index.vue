<template>
  <div class>
    <button class="header">Header!!</button>
    <template v-if="isModal">
      <div class="overlay">
        <Modal @modal="modal" />
      </div>
    </template>
    <button class="modalButton" @click="modal">モーダル</button>
    <button class="footer">Footer!!</button>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Modal from '../components/Modal.vue'
export default Vue.extend({
  components: {
    Modal
  },
  data() {
    return {
      isModal: false
    }
  },
  methods: {
    modal() {
      this.isModal = this.isModal !== true
    }
  }
})
</script>

<style scoped>
.main {
  position: relative;
}
.modalButton {
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
.header {
  position: fixed;
  top: 0px;
  left: 0px;
  right: 0px;
  background: black;
  color: white;
  font-size: 20px;
  width: 100%;
}

.swipe {
  position: absolute;
  padding-top: 20px;
  padding-bottom: 20px;
}
.footer {
  position: fixed;
  bottom: 0px;
  left: 0px;
  right: 0px;
  background: black;
  color: white;
  font-size: 20px;
  width: 100%;
}
</style>