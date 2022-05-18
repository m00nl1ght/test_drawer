<template>
  <div v-if="isOpenModal" class="modal" :class="isMobile ? 'modal_mobile': 'modal_desc'">
    <h1>Hello world</h1>
    <button @click="closeModal">Close</button>
  </div>
</template>

<script>
const MOBILE_BREAKPOINT = 768

export default {
  name: 'HelloWorld',
  props: {
    isOpenModal: Boolean
  },

  data() {
    return {
      width: 0
    }
  },
  
  methods: {
    closeModal() {
      this.$emit('close')
    },

    updateWidth() {
      this.width = window.innerWidth;
    }, 
  },

  computed: {
    isMobile() {
      return this.width < MOBILE_BREAKPOINT
    }
  },

  created() {
    this.updateWidth()

    window.addEventListener('resize', () => this.updateWidth());
  },

  beforeDestroy() {
    window.removeEventListener('resize')
  }
}
</script>


<style scoped>
.modal {
  position: absolute;
  z-index: 1;
 
  background-color: white;
}

.modal_desc {
  height: 50vh;
  width: 50vw;
  padding: 10px;
   border: 1px solid black;
}

.modal_mobile {
  height: 100vh;
  width: 100vw;
}
</style>
