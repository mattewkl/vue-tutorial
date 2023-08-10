<template>
  <div class="space-y-3 text-black text-sm mt-5">
    <div
      v-for="(label, index) in searchPredictions"
      :key="label"
      class="flex items-center"
    >
      <BaseCheckbox
        :id="index"
        :value="label"
        v-bind="$attrs"
        v-model="selectedSearchPredictions"
      >
        {{ label }}
      </BaseCheckbox>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    searchPredictions: Array,
    modelValue: Array
  },
  emits: ['update:modelValue'],
  data () {
    return {
      selectedSearchPredictions: this.modelValue
    }
  },
  watch: {
    selectedSearchPredictions () {
      this.$emit('update:modelValue', this.selectedSearchPredictions)
    }
  }
}
</script>