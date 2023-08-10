<template>
  <BaseModal class="md:w-4/5 max-w-2xl">
    <p class="text-base text-black tracking-wide">Report search predictions</p>
    <TheSearchPredictionsList
      v-model="selectedSearchPredictions"
      :search-predictions="searchPredictions"
    />
    <p class="text-xs text-gray-600 mt-5">The selected predictions are:</p>
    <div class="space-y-3 text-black text-sm mt-5">
      <div
        class="flex items-center"
        v-for="(label, index) in searchPredictionCategories"
        :key="label"
      >
        <input
          type="radio"
          :id="`search-predictions-category-${index}`"
          :value="label"
          class="w-5 h-5 cursor-pointer"
          v-model="selectedSearchPredictionCategory"
        />
        <label
          :for="`search-predictions-category-${index}`"
          class="pl-4 cursor-pointer flex-grow"
          >{{ label }}</label
        >
      </div>
    </div>
    <template #footer="{ close }">
      <BaseButton @click="close" class="ml-auto"> Cancel </BaseButton>
      <BaseButton class="ml-1 text-gray-400 cursor-auto" disabled>
        Report
      </BaseButton>
    </template>
  </BaseModal>
</template>

<script>
import BaseModal from "./BaseModal.vue";
import TheSearchPredictionsList from "./TheSearchPredictionsList.vue";
import BaseButton from "./BaseButton.vue";

export default {
  components: {
    BaseModal,
    TheSearchPredictionsList,
    BaseButton,
  },
  data() {
    return {
      selectedSearchPredictions: [],
      selectedSearchPredictionCategory: null,
      searchPredictionCategories: [
        "Hateful",
        "Sexually Explicit",
        "Violent",
        "Dangerous and harmful activity",
        "Other",
      ],
    };
  },
  props: {
    searchPredictions: Array,
  },
};
</script>
