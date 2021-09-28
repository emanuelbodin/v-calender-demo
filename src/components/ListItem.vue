<template>
  <div
    class="list-item"
    :class="{ selected: isSelected }"
    @click="onSelect(id)"
  >
    <img src="../assets/test.svg" />
    <div class="textContainer">
      <div class="title">{{ title }}</div>
      <div class="subTitle">{{ value }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    id: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
    isSelected: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    onSelect(id) {
      this.$emit('selected', id);
    },
  },
};
</script>

<style scoped>
.list-item {
  display: flex;
  padding: 7px;
  border-radius: 2px 0px 0px 2px;
  margin-top: 2px;
  cursor: pointer;
}
.list-item:hover {
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
}

.selected {
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
  border-right: 3px solid #6a6a6a;
}

.textContainer {
  margin-left: 10px;
  color: #6a6a6a;
  font-size: 15px;
}

.title {
  font-weight: 600;
}

.subTitle {
  font-weight: 500;
  font-size: 13px;
}
</style>