<template>
  <div>
    <div class="modal" :class="{ active: true }">
      <div class="modal-body">
        <div class="left-col">
          <VerticalTab />
        </div>
        <div class="mid-col">
          <CalenderFilter />
          <Calendar />
        </div>
        <div class="right-col">
          <QuickChoices />
          <div class="filterButtonContainer"><Button title="Filtrera" /></div>
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
import CalenderFilter from './CalenderFilter.vue';
import QuickChoices from './QuickChoices.vue';
import Button from './Button.vue';

export default {
  name: 'Modal',
  components: {
    Calendar,
    VerticalTab,
    CalenderFilter,
    QuickChoices,
    Button,
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
  border-radius: 2px;
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
  text-align: center;
  position: absolute;
  right: 0;
  top: 0;
  cursor: pointer;
  border: none;
  outline: none;
  background: none;
  font-size: 1.25rem;
  color: #fff;
  background-color: #16191c;
}

.modal-body {
  display: flex;
  position: relative;
  height: 100%;
}
.left-col {
  width: 15%;
  height: 100%;
}

.mid-col {
  width: 50%;
  margin-top: 20px;
  margin-left: 20px;
}

.right-col {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 35%;
  margin: 20px;
}

.filterButtonContainer {
  align-self: flex-end;
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
