<script>
import TheSearchBtn from "./TheSearchBtn.vue";
import TheSearchInput from "./TheSearchInput.vue";
import TheSearchResults from "./TheSearchResults.vue";

export default {
  components: { TheSearchBtn, TheSearchInput, TheSearchResults },
  data() {
    return {
      keywords: [
        "new york giants",
        "new york alicia keys",
        "new york giants vs washington football",
        "new york",
        "new york song",
        "new york new york frank sinatra",
        "new york jets",
        "new york city",
        "new york giants live",
        "new york state of mind",
        "new york giants vs washington football live",
        "new york giants injury",
        "new york giants live stream",
        "new york accent",
      ],
      query: "",
    };
  },
  computed: {
    results() {
      return this.keywords.filter((result) => {
        return result.includes(this.query);
      });
    },
  },
};
</script>
<template>
  <div class="mr-2 flex w-full">
    <TheSearchInput v-model:query="query" />
    <TheSearchResults v-show="query" :results="results" />
    <TheSearchBtn />
  </div>
</template>

<style></style>
