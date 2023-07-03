<template>
  <div class="relative">
    <button @click="isOpen = !isOpen" class="relative p-2 focus:outline-none">
      <base-icon name="viewGrid" />
    </button>
    <transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transition opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class=" transition ease-out duration-75"
      leave-from-class="transform opacity-100 scale-100"
      leave-to-class="transition opacity-0 scale-95"
    >
      <div
        @keydown.esc="isOpen = false"
        ref="dropdown"
        tabindex="-1"
        v-show="isOpen"
        class="absolute top-9 right-0 sm:left-0 bg-white w-60 border border-t-0 focus:outline-none"
      >
        <section class="py-2 border-b">
          <ul>
            <DropdownListItem label="Youtube TV" />
          </ul>
        </section>
        <section class="py-2 border-b">
          <ul>
            <DropdownListItem label="YouTube Music" />
            <DropdownListItem label="YouTube Kids" />
          </ul>
        </section>
        <section class="py-2">
          <ul>
            <DropdownListItem label="Creator Academy" />
            <DropdownListItem label="YouTube for Artists" />
          </ul>
        </section>
      </div>
    </transition>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import DropdownListItem from "./DropdownListItem.vue";
export default {
  components: { DropdownListItem, BaseIcon },
  data() {
    return {
      isOpen: false,
    };
  },
  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    });
  },
  watch: {
    isOpen() {
      this.$nextTick(() => {
        if (this.isOpen) {
          this.$refs.dropdown.focus();
        }
      });
    },
  },
};
</script>

<style></style>
