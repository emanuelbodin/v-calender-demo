<template>
  <button class="button">{{ title }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    title: {
      type: String,
      required: true,
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
  padding: 5px 30px;
  cursor: pointer;
}
</style>
