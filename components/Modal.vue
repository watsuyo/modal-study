<template>
  <div class="modal" @touchstart="touchstart" @touchend="touchend"></div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data: {
    startYposition: 0,
    startXposition: 0,
    endYPosition: 0,
    endXPosition: 0
  },
  methods: {
    touchstart(event) {
      this.startYposition = event.changedTouches[0].clientY
      this.startXposition = event.changedTouches[0].clientX
    },
    touchend(event) {
      this.endYposition = event.changedTouches[0].clientY
      this.endXposition = event.changedTouches[0].clientX
      this.endYposition - this.startYposition > 100 && this.closeModal()
    },
    closeModal() {
      this.$emit('modal')
    },
    stopEvent() {
      event.stopPropagation()
    }
  }
})
</script>

<style scoped>
.modal {
  position: fixed;
  z-index: 2;
  width: 100%;
  height: 50%;
  padding: 1em;
  bottom: 0;
  background: #fff;
}
</style>