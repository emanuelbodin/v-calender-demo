<template>
  <div>
    <div class="dropdown">
      <DropdownHeader
        :title="title"
        :header="header"
        :isOpen="isOpen"
        @toggle="toggleDropdown"
      />
      <div class="dropdown-content" :class="{ open: isOpen }">
        <div>
          <DropdownRowCheckbox
            v-for="option in options1"
            :id="option.id"
            :key="option.id"
            :checked="option.checked"
            :value="option.value"
          />
        </div>
        <div class="separator" />
        <div>
          <DropdownRowCheckbox
            v-for="option in options2"
            :id="option.id"
            :key="option.id"
            :checked="option.checked"
            :value="option.value"
            @toggle="onToggle"
          />
        </div>
      </div>
    </div>
    <div
      class="overlay"
      :class="{ overlayActive: isOpen }"
      @click="toggleDropdown()"
    />
  </div>
</template>

<script>
import DropdownHeader from './DropdownHeader';
import DropdownRowCheckbox from './DropdownRowCheckbox';
export default {
  name: 'Dropdown',
  components: { DropdownHeader, DropdownRowCheckbox },
  props: {
    title: {
      type: String,
      required: true,
    },
    header: {
      type: String,
      required: true,
    },
    options1: {
      type: Array,
      required: true,
    },
    options2: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    onToggle(id) {
      this.$emit('toggle', id);
    },
  },
};
</script>

<style scoped>
.dropdown {
  width: 100%;
  min-width: 100px;
  z-index: 10;
  position: relative;
}

.dropdown-content {
  background: #f8f8f8;
  position: absolute;
  left: 0;
  top: calc(100% + 0.7rem);
  background-color: #fff;
  border-radius: 0px 0px 2px 2px;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
  opacity: 0;
  pointer-events: none;
  transform: translateY(-10px);
  transition: opacity 150ms ease-in-out, transform 150ms ease-in-out;
  font-weight: 600;
  font-size: 12px;
  color: #6a6a6a;
  overflow-y: scroll;
  max-height: 200px;
}
.dropdown-content.open {
  opacity: 1;
  pointer-events: auto;
}

.separator {
  margin-left: 5%;
  margin-right: 5%;
  border-bottom: 1px solid #efefef;
}

.overlay {
  position: fixed;
  opacity: 0;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.overlayActive {
  pointer-events: all;
}
</style>