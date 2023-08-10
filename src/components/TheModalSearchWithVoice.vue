<template>
  <BaseModal with-close-button>
    <p class="text-2xl mb-52">{{ text }}</p>
    <the-button-search-with-voice @change-text="text = $event"/>
  </BaseModal>
</template>

<script>
import BaseModal from './BaseModal.vue'
import TheButtonSearchWithVoice from './TheButtonSearchWithVoice.vue'

const STATUS_IDLE = "idle"
const STATUS_LISTENING = "listening"
const STATUS_RECORDING = "recording"
const STATUS_QUIET = "quiet"


export default {
  components: {
    BaseModal,
    TheButtonSearchWithVoice
  },

  data () {
    return {
      text: null
    }
  },

  
}
</script>