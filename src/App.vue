<template>
  <div id="app">
    <button @click="openModal">Open modal</button>
    
    <HelloWorld 
      :isOpenModal="isOpenModal"
      @close="isOpenModal = false"
    />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },

  data() {
    return {
      isOpenModal: false
    }
  },

  methods: {
    openModal() {
      this.isOpenModal = true
    }
  }
}
</script>

<style>
body {
  margin: 0;
}

#app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  position: relative;
}
</style>
