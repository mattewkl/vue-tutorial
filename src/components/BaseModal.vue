<template>
  <div class="fixed inset-0 z-10 bg-black bg-opacity-80 focus:outline-none"  tabindex="-1" @click.self="close" @keydown.esc="close">
    <div class="bg-white max-w-sm mx-auto my-8">
      <div class="p-2 text-right">
        <BaseModalButtonClose @click="close" />
        
      </div>
      <div class="p-6">
        sdfhsodfgj dflkghods; kgasdio f
      </div>
    </div>
  </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
import BaseModalButtonClose from './BaseModalButtonClose.vue'
export default {
  components: { BaseIcon, BaseModalButtonClose },
  emits: ['close'],
  methods: {
    close() {
      this.$emit('close')
    }
  },
  mounted() {
    this.$el.focus()
  }

}
</script>

<style>

</style>