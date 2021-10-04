<template>
  <div class="app">
    <div class="container">
      <IconButton
        iconSrc="@/assets/calendar.svg"
        title="Kalender"
        subtitle="Aug 1-31 (Mån-Fre) "
        @click="toggleModal"
      />
      <div class="col">
        <DropdownCheckbox
          :title="dropdownTitle"
          :header="dropdownHeader"
          :options1="dropdownOptions1"
          :options2="dropdownOptions2"
          @toggle="onToggleDropdown"
        />
      </div>
      <div class="col">
        <Dropdown
          :title="dropdownTitle"
          :header="dropdownHeaderSelect"
          :options="dropdownOptions3"
          @select="onSelect"
        />
      </div>
    </div>
    <Modal :isOpen="modalOpen" @closeModal="toggleModal" />
  </div>
</template>

<script>
import Modal from './components/Modal.vue';
import IconButton from './components/IconButton.vue';
import Dropdown from './components/Dropdown/Dropdown';
import DropdownCheckbox from './components/Dropdown/DropdownCheckbox';

export default {
  name: 'App',
  components: {
    Modal,
    IconButton,
    Dropdown,
    DropdownCheckbox,
  },
  data() {
    return {
      modalOpen: false,
      dropdownTitle: 'Byggnad',
      dropdownHeader: '--Välj--',
      dropdownOptions1: [
        { id: '11', value: 'Bokningsbara rum', checked: false },
        { id: '12', value: 'Icke bokningsbara rum', checked: false },
      ],
      dropdownOptions2: [
        { id: '21', value: 'Alla', checked: true },
        { id: '22', value: 'Gemensamma utrymmen', checked: true },
        { id: '23', value: 'Laboratorier', checked: true },
        { id: '24', value: 'Lärosalar & Grupprum', checked: true },
        { id: '25', value: 'Övrigt', checked: true },
      ],
      dropdownOptions3: [
        { id: '31', value: 'Option 1', selected: false },
        { id: '32', value: 'Option 2', selected: false },
        { id: '33', value: 'Option 3', selected: false },
        { id: '34', value: 'Option 4', selected: false },
        { id: '35', value: 'Option 5', selected: false },
      ],
      selected: null,
    };
  },
  computed: {
    dropdownHeaderSelect() {
      return this.selected == null ? 'Alla' : this.selected.value;
    },
  },
  methods: {
    toggleModal() {
      this.modalOpen = !this.modalOpen;
    },
    onToggleDropdown(id) {
      this.dropdownOptions2 = this.dropdownOptions2.map((el) => {
        if (el.id === id) el.checked = !el.checked;
        return el;
      });
    },
    onSelect(id) {
      this.selected = this.dropdownOptions3.find((el) => el.id === id);
      this.dropdownOptions3 = this.dropdownOptions3.map((el) => {
        if (el.id === id) el.selected = true;
        else el.selected = false;
        return el;
      });
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
  width: 60%;
  margin: auto;
}

.container {
  display: flex;
  justify-content: space-around;
}

.col {
  width: 175px;
}
</style>
