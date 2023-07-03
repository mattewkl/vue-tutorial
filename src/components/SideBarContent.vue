<template>
  <sidebar-section><ul>
        <SidebarNavItem label="Home" icon="home" is-active />
        <SidebarNavItem label="Trending" icon="fire" />
        <SidebarNavItem label="Subscriptions" icon="collection" />
      </ul></sidebar-section>
    <sidebar-section>
      <ul>
        <SidebarNavItem label="Library" icon="duplicate" />
        <SidebarNavItem label="History" icon="clock" />
      </ul>
    </sidebar-section>
    <sidebar-section class="px-8 py-4 font-medium leading-5 border-b">
      <span class="text-sm">
        Sign in to like videos, comment, and subscribe.
      </span>
      <button-login class="focus:outline-none flex items-center px-2 py-0.5 mt-3 text-sm text-blue-700 uppercase border border-blue-700 rounded-sm" ></button-login>
    </sidebar-section>
    <sidebar-section>
      <sidebar-section-heading label="Best of Youtube"/>
      <ul>
        <SidebarNavItem label="Music" icon="musicNote" />
        <SidebarNavItem label="Sports" icon="speakerphone" />
        <SidebarNavItem label="Gaming" icon="puzzle" />
        <SidebarNavItem label="Movies" icon="film" />
        <SidebarNavItem label="News" icon="newspaper" />
        <SidebarNavItem label="Live" icon="statusOnline" />
        <SidebarNavItem label="360&deg; Video" icon="eye" />
      </ul>
    </sidebar-section>
    <sidebar-section>
      <ul>
        <SidebarNavItem label="Browse Channels" icon="plusCircle" />
      </ul>
    </sidebar-section>
    <section class="py-2 border-b">
      <sidebar-section-heading label="More from YouTube"/>
      <ul>
        <SidebarNavItem label="YouTube Premium" icon="play" />
        <SidebarNavItem label="Live" icon="statusOnline" />
      </ul>
    </section>
    <sidebar-section>
      <ul>
        <SidebarNavItem label="Settings" icon="cog" />
        <SidebarNavItem label="Report history" icon="flag" />
        <SidebarNavItem label="Help" icon="questionMarkCircle" />
        <SidebarNavItem label="Send feedback" icon="annotation" />
      </ul>
    </sidebar-section>
    <sidebar-section class="px-6 py-4 text-xs font-semibold space-y-4">
    </sidebar-section>
</template>

<script>
import ButtonLogin from './ButtonLogin.vue'
import SidebarNavItem from './SidebarNavItem.vue'
import SidebarSection from './SidebarSection.vue'
import SidebarSectionHeading from './SidebarSectionHeading.vue'
export default { 
  components: { SidebarNavItem, ButtonLogin, SidebarSectionHeading, SidebarSection, }

}
</script>

<style>

</style>