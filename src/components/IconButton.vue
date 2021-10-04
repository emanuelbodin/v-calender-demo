<template>
  <button class="button" @click="click">
    <div class="container">
      <img class="icon" src="../assets/calendar.svg" />
      <div class="title">{{ title }}</div>
      <div class="subtitle">{{ subtitle }}</div>
    </div>
  </button>
</template>

<script>
export default {
  name: 'IconButton',
  props: {
    title: {
      type: String,
      required: true,
    },
    subtitle: {
      type: String,
      default: 'false',
    },
    iconSrc: {
      type: String,
      required: true,
    },
  },
  methods: {
    click() {
      this.$emit('click');
    },
  },
};
</script>

<style scoped>
.button {
  background-color: #f8f8f8;
  color: #6a6a6a;
  border-radius: 2px;
  border: 2px solid #efefef;
  cursor: pointer;
}
.button:hover {
  background-color: #efefef;
}

.container {
  padding: 5px;
  display: flex;
  gap: 20px;
}

.icon {
  display: block;
}

.title {
  font-weight: 600;
  font-size: 15px;
}

.subtitle {
  font-weight: 500;
  font-size: 15px;
}
</style>
