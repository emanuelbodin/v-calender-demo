<template>
  <div class="dropdown-row" @click="onSelect(id)">
    {{ value }}
  </div>
</template>

<script>
export default {
  name: 'DropdownRowCheckbox',
  props: {
    id: {
      type: String,
      required: true,
    },
    selected: {
      type: Boolean,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    onSelect(id) {
      this.$emit('select', id);
    },
  },
};
</script>

<style scoped>
.dropdown-row {
  width: 100%;
  display: flex;
  align-items: center;
  padding: 10px;
  cursor: pointer;
}

.dropdown-row:hover {
  background-color: #cccccc;
}
</style>