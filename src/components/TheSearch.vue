<script>
import TheSearchBtn from './TheSearchBtn.vue';
import TheSearchInput from "./TheSearchInput.vue";

export default {
  components: { TheSearchBtn, TheSearchInput },};
</script>
<template>
  <div class=" mr-2 flex w-full ">
    <TheSearchInput />
    <TheSearchBtn/>
  </div>
</template>

<style></style>
