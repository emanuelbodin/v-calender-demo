<template>
  <div class="dropdown-row">
    <div class="checkbox-container">
      <Checkbox :id="id" :checked="checked" @toggle="onToggle" />
    </div>
    {{ value }}
  </div>
</template>

<script>
import Checkbox from '../Checkbox';

export default {
  name: 'DropdownRowCheckbox',
  components: {
    Checkbox,
  },
  props: {
    id: {
      type: String,
      required: true,
    },
    checked: {
      type: Boolean,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    onToggle(id) {
      this.$emit('toggle', id);
    },
  },
};
</script>

<style scoped>
.dropdown-row {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px;
}

.checkbox-container {
  width: 12px;
  height: 12px;
}
</style>