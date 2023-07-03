<template>
  <aside
    class="hidden xl:block w-64 max-h-screen overflow-auto fixed top-0 pt-12 bg-white z-20"
  >
    <s-ide-bar-content/>
  </aside>
</template>

<script>

import SIdeBarContent from './SIdeBarContent.vue'
export default {
  components: { SIdeBarContent },
  name: 'TheSidebar',

}
</script>

<style>

</style>
