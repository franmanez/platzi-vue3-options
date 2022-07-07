<template>
  <div>
    <button @click="toggle">Modal</button>
    <teleport to="body">
      <div v-show="show" class="modal">
        <h2>Titulo</h2>
        <p>Esto es solo simple texto en un parrafo</p>
        <button @click="toggle">cerrar</button>
      </div>
    </teleport>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Menu',
  data () {
    return {
      show: false
    }
  },

  methods: {
    toggle () {
      this.show = !this.show
    }
  }
}
</script>
