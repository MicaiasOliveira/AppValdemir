<template>
  <div class="d-flex justify-content-center align-items-stretch">
    <transition name="fade" mode="out-in">
      <div class="LoginBox" show v-if="!RegisterLogin">
        <h1 class="align-self-center m-3">Olá Valdemir!</h1>
        <b-form-input class="mb-2 opacity-50 rounded-4" v-model="text" placeholder="Digite seu login"></b-form-input>
        <b-form-input class="mb-3 opacity-50 rounded-4" v-model="password" placeholder="Digite sua senha"></b-form-input>
        <b-button class="mb-2 rounded-4 text-monospace" @click="loginMenu">Entrar</b-button>
        <div class="d-flex justify-content-between">
          <b-button variant="outline-dark" class="opacity-75">Recuperer Senha</b-button>
          <b-button variant="outline-dark" class="opacity-75" @click="RegisterLogin = !RegisterLogin">Registrar</b-button>
        </div>
      </div>

      <div class="RegisterBox" show v-if="RegisterLogin">
        <h1 class="align-self-center m-3">Olá Valdemir!</h1>
        <b-form-input class="mb-2 opacity-50 rounded-4" v-model="usuario.nome" placeholder="Nome e Sobrenome"></b-form-input>
        <b-form-input class="mb-2 opacity-50 rounded-4" v-model="usuario.celular" placeholder="Número de Celular"></b-form-input>
        <b-form-input class="mb-2 opacity-50 rounded-4" v-model="usuario.login" placeholder="Digite seu login"></b-form-input>
        <b-form-input class="mb-2 opacity-50 rounded-4" v-model="usuario.senha" placeholder="Digite sua senha"></b-form-input>
        <b-form-input class="mb-3 opacity-50 rounded-4" placeholder="Repita sua senha"></b-form-input>
        <b-button class="mb-2 rounded-4 text-monospace" @click="salvar">Registrar</b-button>
      </div>
    </transition>
  </div>
</template>

<script>
import EventBus from '@/eventBus'
export default {
  data() {
    return {
      RegisterLogin: false,
      usuario: {
        nome: '',
        celular: '',
        login: '',
        senha: ''
      }
    }
  },
  methods: {
      loginMenu() {
        this.logado = true
        EventBus.$emit('usuarioLogado', this.logado)
      },
      salvar() {
        this.$http.post('usuarios.json', this.usuario)
          .then(resp => {
            this.usuario.nome = ''
            this.usuario.celular = ''
            this.usuario.login = ''
            this.usuario.senha = ''
            alert('Cadastro realizado com Sucesso!!!')
            this.RegisterLogin = !this.RegisterLogin
            return resp
          })
      }
  },
  name: 'LoginView',
}
</script>

<style>
.LoginBox {
  display: flex;
  flex-direction: column;
  margin-top: 11%;
}

.RegisterBox {
  display: flex;
  flex-direction: column;
  margin-top: 8%;
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