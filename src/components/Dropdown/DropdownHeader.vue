<template>
  <fieldset class="dropdown-header" @click="click()">
    <legend class="dropdown-title">{{ title }}</legend>
    <div class="dropdown-header-content">
      <div>{{ header }}</div>
      <div :class="{ rotated: isOpen }">
        <img src="../../assets/dropdown-arrow.svg" />
      </div>
    </div>
  </fieldset>
</template>

<script>
export default {
  name: 'DropdownHeader',
  props: {
    title: {
      type: String,
      required: true,
    },
    header: {
      type: String,
      required: true,
    },
    isOpen: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    click() {
      this.$emit('toggle');
    },
  },
};
</script>

<style scoped>
.dropdown-header {
  width: 100%;
  border-radius: 2px 2px 0px 0px;
  border: 0;
  box-sizing: border-box;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
  font-weight: 600;
  font-size: 15px;
  color: #707070;
  cursor: pointer;
}

.dropdown-title {
  font-weight: 600;
  font-size: 10px;
  background-color: #fff;
}

.dropdown-header-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.rotated {
  transform: rotate(-180deg);
}
</style>