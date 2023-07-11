<script>
import TheSearchBtn from './TheSearchBtn.vue';
import TheSearchInput from "./TheSearchInput.vue";
import TheSearchResults from './TheSearchResults.vue';

export default {
  components: { TheSearchBtn, TheSearchInput, TheSearchResults },};
</script>
<template>
  <div class=" mr-2 flex w-full ">
    <TheSearchInput />
    <TheSearchResults/>
    <TheSearchBtn/>
  </div>
</template>

<style></style>
