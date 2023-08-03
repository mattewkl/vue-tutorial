<template>
  <header :class="classes">
    <div :class="leftSideClasses">
      <div class="flex items-center xl:w-64 xl:bg-white pl-4">
        <button
          @click="$emit('toggleSidebar')"
          class="mr-3 sm:ml-2 sm:mr-6 focus:outline-none"
        >
          <BaseIcon name="menu" />
        </button>
        <LogoMain />
      </div>
    </div>
    <TheSearchWrapper
      v-show="isSearchShown"
      :isSmallScreen="isSmallScreen"
      @close="closeMobileSearch"
      @open-voice-modal="isVoiceModalOpen = true"
    >
    </TheSearchWrapper>

    <div :class="rightSideClasses">
      <BaseTooltip text="Search with your voice">
        <button class="sm:hidden p-2 focus:outline-none" @click="isVoiceModalOpen = true">
          <BaseIcon name="microphone" class="w-5 h-5" />
        </button>
      </BaseTooltip>
      <BaseTooltip text="Search">
        <button
          @click.stop="isMobileSearchActive = true"
          class="sm:hidden p-2 focus:outline-none"
        >
          <BaseIcon name="search" class="w-5 h-5" />
        </button>
      </BaseTooltip>
      <TheDropDownApps />
      <TheDropdownSettings />
      <ButtonLogin />
    </div>
  </header>
  <the-modal-search-with-voice @close="isVoiceModalOpen = false" v-if="isVoiceModalOpen"/>
</template>

<script>
import { computed } from "vue";
import BaseIcon from "./BaseIcon.vue";
import BaseTooltip from "./BaseTooltip.vue";
import LogoMain from "./LogoMain.vue";
import ButtonLogin from "./ButtonLogin.vue";
import TheSearchWrapper from "./TheSearchWrapper.vue";
import TheDropDownApps from "./TheDropDownApps.vue";
import TheDropdownSettings from "./TheDropdownSettings.vue";
import TheModalSearchWithVoice from './TheModalSearchWithVoice.vue';

export default {
  components: {
    BaseIcon,
    BaseTooltip,
    LogoMain,
    ButtonLogin,
    TheSearchWrapper,
    TheDropDownApps,
    TheDropdownSettings,
    TheModalSearchWithVoice,
  },

  emits: {
    toggleSidebar: null,
  },
  data() {
    return {
      isSmallScreen: false,
      isMobileSearchActive: false,
      isVoiceModalOpen: false,

      classes: [
        "flex",
        "justify-between",
        "w-full",
        "bg-white",
        "bg-opacity-95",
      ],
    };
  },

  computed: {
    isMobileSearchShown() {
      return this.isSmallScreen && this.isMobileSearchActive;
    },
    isSearchShown() {
      return !this.isSmallScreen || this.isMobileSearchActive;
    },
    opacity() {
      return this.isMobileSearchShown ? "opacity-0" : "opacity-100";
    },
    leftSideClasses() {
      return ["lg:w-1/4", "flex", this.opacity];
    },
    rightSideClasses() {
      [
        "flex",
        "items-center",
        "justify-end",
        "lg:w-1/4",
        "sm:space-x-3",
        "p-2",
        "sm:px-4",
        this.opacity,
      ];
    },
  },

  mounted() {
    this.onResize();

    window.addEventListener("resize", this.onResize);
  },

  methods: {
    onResize() {
      if (window.innerWidth < 640) {
        this.isSmallScreen = true;
        return;
      }

      this.closeMobileSearch();
      this.isSmallScreen = false;
    },

    closeMobileSearch() {
      this.isMobileSearchActive = false;
    },
  },
  provide() {
    return {
      isMobileSearchActive: computed(() => this.isMobileSearchActive),
    };
  },
};
</script>
