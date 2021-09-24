<template>
  <div>
    <div class="modal" :class="{ active: true }">
      <div class="modal-body">
        <div class="left-container">
          <VerticalTab />
        </div>
        <div class="mid-container">
          <Calendar />
        </div>
        <button class="close-button" @click="closeModal">&times;</button>
      </div>
    </div>
    <div id="overlay" :class="{ active: true }" @click="closeModal"></div>
  </div>
</template>

<script>
import Calendar from './Calendar.vue';
import VerticalTab from './VerticalTab.vue';

export default {
  name: 'Modal',
  components: {
    Calendar,
    VerticalTab,
  },
  props: {
    isOpen: {
      type: Boolean,
      deafult: false,
    },
  },
  methods: {
    closeModal() {
      this.$emit('closeModal');
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(0);
  transition: 200ms ease-in-out;
  border: 1px solid black;
  border-radius: 10px;
  z-index: 10;
  background-color: white;
  width: 800px;
  height: 400px;
  max-width: 90%;
  max-height: 80%;
}

.modal.active {
  transform: translate(-50%, -50%) scale(1);
}

.close-button {
  justify-self: end;
  align-self: start;
  cursor: pointer;
  border: none;
  outline: none;
  background: none;
  font-size: 1.25rem;
  font-weight: bold;
}

.modal-body {
  display: flex;
  height: 100%;
}

.mid-container {
  width: 70%;
}

.left-container {
  width: 16%;
  height: 100%;
}

#overlay {
  position: fixed;
  opacity: 0;
  transition: 200ms ease-in-out;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  pointer-events: none;
}

#overlay.active {
  opacity: 1;
  pointer-events: all;
}
</style>
