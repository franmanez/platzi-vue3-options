<template>
  <p>{{ text }}</p>
  <p>{{ algo }}</p>
  <img alt="Vue logo" src="./assets/logo.png">
  <Modal></Modal>
  <button @click="show = !show">Menu</button>
  <transition name="fade">
    <Menu v-show="show"></Menu>
  </transition>
  <hr>
  <HelloWorld msg="Componente Normal"/>

  <h1>COMPONENTES DINÁMICOS</h1>
  <component v-bind:is="componente"></component>

  <HelloWorldAsync msg="Componentes Dinámicos"/>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import { defineAsyncComponent } from 'vue'
import Menu from '@/components/Menu'
import Modal from '@/components/Modal'

import base from '@/mixins/base'

const HelloWorldAsync = defineAsyncComponent(() => import('./components/HelloWorld'))

export default {
  name: 'App',
  mixins: [base],
  components: {
    Modal,
    Menu,
    HelloWorld,
    HelloWorldAsync
  },
  data () {
    return {
      text: 'Hola Vue',
      show: false,
      componente: 'HelloWorld'
    }
  },
  beforeCreate () {
    console.log('beforeCreate', this.$data, this.$el)
  },
  created () {
    console.log('created', this.$data, this.$el)
  },
  mounted () {
    console.log('mounted', this.$data, this.$el)
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
