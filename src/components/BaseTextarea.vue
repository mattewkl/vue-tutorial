<template>
  <textarea
    v-bind="$attrs"
    maxlength="limit"
    v-model="searchPredictionDetails"
    placeholder="Provide additional details (options)"
    class="border rounded-sm pt-2 pb-5 px-2 resize-none focus:outline-none w-full overflow-hidden"
    ref="textarea"
  />
  <div class="absolute bottom-2 right-2 text-xs text-gray-600">
    {{ counter }}
  </div>
</template>

<script>
export default {
  props: {
    modelValue: String,
    limit: Number,
  },
  data() {
    return {
      searchPredictionsDetails: this.modelValue
    };
  },
  computed: {
    counter() {return `${this.modelValue.length} / ${this.limit}`}
  },
  mounted () {
    this.adjustHeight()
  },
  methods: {
    adjustHeight () {
      this.$refs.textarea.style.height = 'auto'
      this.$refs.textarea.style.height = `${this.$refs.textarea.scrollHeight}px`
    }}
};
</script>
