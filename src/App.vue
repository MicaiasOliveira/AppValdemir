<template>
  <div>
    <img class="wallpaper" src="../src/assets/wallpaper.jpg" alt="">
    <transition name="fade" mode="out-in">
      <header-view show v-if="logado"></header-view>
      <login-view show v-if="!logado"></login-view>
    </transition>
  </div>
</template>

<script>
import LoginView from './views/LoginView.vue'
import HeaderView from './views/HeaderView.vue'
import EventBus from '@/eventBus'
export default {
  data() {
    return {
      logado: false
    }
  },
  components: {
    LoginView,
    HeaderView
  },
  created() {
    EventBus.$on('usuarioLogado', logado => {
      this.logado = logado
    })
  }
}
</script>

<style>
div {
  position: relative;
}
.wallpaper {
  position: absolute;
  height: 100vh;
  width: 100%;
}

.fade-enter-active {
  animation: slide-in 1s ease;
  transition: opacity 1s;
}

.fade-leave-active {
  animation: slide-out 1s ease;
  transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
