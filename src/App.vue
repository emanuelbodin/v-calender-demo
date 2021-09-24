<template>
  <div class="app">
    <button @click="toggleModal">Calendar</button>
    <Modal :isOpen="modalOpen" @closeModal="toggleModal" />
  </div>
</template>

<script>
import Modal from './components/Modal.vue';
export default {
  name: 'App',
  components: {
    Modal,
  },
  data() {
    return {
      modalOpen: false,
    };
  },
  methods: {
    toggleModal() {
      this.modalOpen = !this.modalOpen;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@600&display=swap');

* {
  font-family: 'Raleway', sans-serif;
  display: border-box;
}
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
}
</style>
