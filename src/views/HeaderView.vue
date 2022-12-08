<template>
  <nav class="p-3 navbar navbar-expand-lg navbar-dark bg-dark">
    <SideBar />
    <NavMenu />
  </nav>
</template>

<script>
import SideBar from '../components/SideBar.vue'
import NavMenu from '../components/NavMenu.vue'
export default {
  components: {
    SideBar,
    NavMenu
  }
}
</script>
