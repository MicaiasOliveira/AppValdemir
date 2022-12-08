<template>
  <div>
    <b-button v-b-toggle.sidebar-footer><b-icon icon="person-lines-fill"></b-icon></b-button>
    <b-sidebar id="sidebar-footer" aria-label="Sidebar with custom footer" bg-variant="secondary" no-header shadow backdrop backdrop-variant="dark">
      <template #footer="{ hide }">
       <div class="d-flex justify-content-between bg-dark text-light px-3 py-2">
        <strong class="mr-auto">Footer</strong>
        <b-button size="sm" @click="hide">Fechar</b-button>
       </div>
      </template>
      <div class="px-3 py-2">
        <h4>Olá, Valdemir!</h4>
        <nav class="mb-3">
            <b-nav class="text-dark" vertical>
              <b-nav-item active @click="hide">Active</b-nav-item>
              <b-nav-item href="#link-1" @click="hide">Link</b-nav-item>
              <b-nav-item href="#link-2" @click="hide">Another Link</b-nav-item>
            </b-nav>
        </nav>
      </div>
    </b-sidebar>
  </div>
</template>

<script>
export default {
    name: 'SideBar'
}
</script>

<style>

</style>