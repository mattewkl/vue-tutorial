<template>
  <textarea
    v-bind="$attrs"
    v-model="searchPredictionDetails"
    placeholder="Provide additional details (options)"
    class="border rounded-sm pt-2 pb-5 px-2 resize-none focus:outline-none w-full"
  />
</template>

<script>
export default {
  props: {
    modelValue: String,
  },
  data() {
    return {
      searchPredictionsDetails: this.modelValue
    };
  },
};
</script>
