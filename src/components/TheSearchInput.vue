<template>
  <div class="relative w-full">
    <input
      type="text"
      placeholder="Search"
      :class="classes"
      :value="query"
      ref="input"
      @focus="setState(true)"
      @blur="setState(false)"
      @keyup.esc="handleEsc"
      @click="setState(true)"
      @input="updateQuery($event.target.value)"
    />
    <button
      class="absolute top-0 right-0 h-full px-3 focus:outline-none"
      v-show="query"
      @click="clear()"
    >
      <BaseIcon name="x" class="w-5 w-5" />
    </button>
  </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'

export default {
  components: {
    BaseIcon
  },

  props: ['query', 'hasResults'],

  emits: ['update:query', 'change-state'],

  data () {
    return {
      classes: [
        'w-full',
        'h-full',
        'px-3',
        'shadow-inner',
        'rounded-bl-sm',
        'rounded-tl-sm',
        'border',
        'border-gray-300',
        'focus:border-blue-700',
        'focus:outline-none'
      ],
      isActive: false
    }
  },

  mounted () {
    if (window.innerWidth < 640) {
      this.$el.focus()
    }
  },

  methods: {
    updateQuery (query) {
      this.$emit('update:query', query)
      this.setState(this.isActive) 
    }, 
    setState(isActive) {
      this.isActive = isActive
      this.$emit('change-state', isActive)
    },
    handleEsc() {
      this.removeSelection();
      if (this.isActive && this.hasResults) {
        this.setState(false)
      }
      else {
        this.$refs.input.blur()
      }
    },
    removeSelection() {
      const end = this.$refs.input.value.length
      this.$refs.input.setSelectionRange(end, end)
    }, 
    clear() {
      this.updateQuery('')
      this.$refs.input.focus()
    }
  }


}
</script>