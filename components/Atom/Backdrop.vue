<template>
  <div class="backdrop" @touchstart="touchstart" @touchend="touchend" />
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      startYposition: 0,
      startXposition: 0,
      endYPosition: 0,
      endXPosition: 0
    }
  },
  methods: {
    touchstart(event) {
      this.startYposition = event.changedTouches[0].clientY
      this.startXposition = event.changedTouches[0].clientX
    },
    touchend(event) {
      this.endYposition = event.changedTouches[0].clientY
      this.endXposition = event.changedTouches[0].clientX
      this.endYposition - this.startYposition > 100 && this.closeBackdrop()
    },
    closeBackdrop() {
      this.$emit('backdrop')
    },
    stopEvent() {
      event.stopPropagation()
    }
  }
})
</script>

<style scoped>
.backdrop {
  position: fixed;
  z-index: 2;
  width: 100%;
  height: 50%;
  padding: 1em;
  bottom: 0;
  background: #fff;
}
</style>
