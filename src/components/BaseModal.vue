<template>
  <div :class="classes" tabindex="-1" @keydown.esc="close">
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
    <div v-if="isOpen" class="relative bg-white  w-full sm:w-2/3 m-8 overflow-auto" style="max-height: calc(100vh - 64px)">
      <div v-if="withCloseButton" class="p-2 text-right">
        <BaseModalButtonClose @click="close" />
      </div>
      <div class="p-6"><slot /></div>
      <div class="flex border-t border-gray-300 py-2" v-if="$slots.footer"><slot name="footer" :close="close"/></div>
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
      this.isOpen = false;
      setTimeout(() => this.$emit("close"), 100);
    },
  },
  mounted() {
    this.$el.focus();
  },
  data() {
    return {
      isOpen: true,
      classes: [
        "focus:outline-none",
        "z-30",
        "inset-0",
        "fixed",
        "flex",
        "justify-center",
        "items-start",
        "mx-auto"
      ],
    };
  },
  props: {
    withCloseButton: Boolean,
  },
};
</script>

<style></style>
