<template>
  <teleport to="body">
    <base-modal @close="$emit('close')">
      <p class="text-2xl mb-52">Microphone off try again</p>
      <button
        class="w-16 h-16 mx-auto bg-gray-300 rounded-full text flex justify-center relative focus:outline-none items-center"
      >
      
        <BaseIcon name="microphone" />
      </button>
      <div class="text-center text-sm text-grey-500 mt-4">Tap the mic</div>
    </base-modal>
  </teleport>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import BaseModal from "./BaseModal.vue";
export default {
  components: { BaseModal, BaseIcon },
};
</script>

<style></style>
