<template>
  <transition
    enter-active-class="transition-opacity ease-linear duration-200"
    enter-from-class="opacity-0"
    enter-to-class="opacity-100"
    leave-active-class="transition-opacity ease-linear duration-200"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0"
  >
    <TheSideBarMobileOverlay v-show="isOpen" @click="isOpen = false" />
  </transition>
  <transition
    enter-active-class="transition ease-in-out duration-200 transform"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="transition ease-in-out duration-200 transform"
    leave-from-class="translate-x-0"
    leave-to-class="-translate-x-full"
  >
    <aside
    v-show="isOpen"
    @keydown.esc="$emit('close')"
    ref="mobileSidebar"
    tabindex="-1"
    class="w-64 max-h-screen overflow-auto bg-white fixed z-30 outline-none"
    >
      <section class="flex items-center p-4 border-b sticky top-0 bg-white">
        <button @click="$emit('close')" class="ml-2 mr-6 focus:outline-none">
          <base-icon name="menu"></base-icon>
        </button>
        <a href="#">
          <logo-main></logo-main>
        </a>
      </section>
      <s-ide-bar-content></s-ide-bar-content>
    </aside>
  </transition>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import LogoMain from "./LogoMain.vue";
import SIdeBarContent from "./SIdeBarContent.vue";
import TheSideBarMobileOverlay from "./TheSIdeBarMobileOverlay.vue";
export default {
  components: { SIdeBarContent, LogoMain, BaseIcon, TheSideBarMobileOverlay },
  name: "TheSideBarMobile",
  props: {
    isOpen: Boolean,
  },
  emits: {
    close: null,
  },
  watch: {
    isOpen() {
      this.$nextTick(() => {
        if (this.isOpen) {
          this.$refs.mobileSidebar.focus();
        }
      });
    },
  },
};
</script>

<style></style>
