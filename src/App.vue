<template>
  <img alt="Vue logo" src="./assets/logo.png">

  <button @click="show = !show">Menu</button>
  <transition name="fade">
    <Menu v-show="show"></Menu>
  </transition>
  <hr>
  <h1>COMPONENTES NORMAL</h1>
  <HelloWorld msg="Componente Normal"/>

  <h1>COMPONENTES DINÁMICOS</h1>
  <component v-bind:is="componente"></component>

  <h1>COMPONENTES ASÍNCRONOS</h1>
  <HelloWorldAsync msg="Componentes Dinámicos"/>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import { defineAsyncComponent } from 'vue'
import Menu from '@/components/Menu'

const HelloWorldAsync = defineAsyncComponent(() => import('./components/HelloWorld'))

export default {
  name: 'App',
  components: {
    Menu,
    HelloWorld,
    HelloWorldAsync
  },
  data () {
    return {
      show: false,
      componente: 'HelloWorld'
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  background: red;
}

.fade-leave-active,
.fade-enter-active{
  transition: opacity 1.5s ease;
}

</style>
