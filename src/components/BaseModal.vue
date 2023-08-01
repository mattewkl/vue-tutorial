<template>
  <div
    :class="classes"
    tabindex="-1"
    @keydown.esc="close"
  >
    <transition
      appear
      enter-active-class=" ease-out duration-200"
      enter-from-class=" opacity-0"
      enter-to-class=" opacity-100"
      leave-active-class=" ease-in duration-100"
      leave-from-class=" opacity-100"
      leave-to-class=" opacity-0"
    >
      <BaseModalOverlay v-if="isOpen" @click="close" />
    </transition>
    <div v-if="isOpen" class="relative bg-white max-w-sm mx-auto my-8">
      <div class="p-2 text-right">
        <BaseModalButtonClose @click="close" />
      </div>
      <div class="p-6">sdfhsodfgj dflkghods; kgasdio f</div>
    </div>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import BaseModalButtonClose from "./BaseModalButtonClose.vue";
import BaseModalOverlay from "./BaseModalOverlay.vue";
export default {
  components: { BaseIcon, BaseModalButtonClose, BaseModalOverlay },
  emits: ["close"],
  methods: {
    close() {
      this.isOpen = false
      setTimeout(() => this.$emit("close"), 100);
      
    },
  },
  mounted() {
    this.$el.focus();
  },
  data() {
    return {
    isOpen: true,
    classes: ['focus:outline-none', 'z-30', 'inset-0', 'fixed']
    }
  }
};
</script>

<style></style>
