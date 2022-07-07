<template>
  <img alt="Vue logo" src="./assets/logo.png">
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

const HelloWorldAsync = defineAsyncComponent(() => import('./components/HelloWorld'))

export default {
  name: 'App',
  components: {
    HelloWorld,
    HelloWorldAsync
  },
  data () {
    return {
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
</style>
