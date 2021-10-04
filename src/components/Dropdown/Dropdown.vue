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
        <DropdownRow
          v-for="option in options"
          :id="option.id"
          :key="option.id"
          :selected="option.selected"
          :value="option.value"
          @select="onSelect"
        />
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
import DropdownRow from './DropdownRow';
export default {
  name: 'Dropdown',
  components: { DropdownHeader, DropdownRow },
  props: {
    title: {
      type: String,
      required: true,
    },
    header: {
      type: String,
      required: true,
    },
    options: {
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
    onSelect(id) {
      this.isOpen = false;
      this.$emit('select', id);
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
  width: 100%;
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