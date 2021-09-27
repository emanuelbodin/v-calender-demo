<template>
  <div>
    <div class="title">Snabbval:</div>
    <ListItem
      v-for="item in listItems"
      :id="item.id"
      :key="item.value"
      :title="item.title"
      :value="item.value"
      :isSelected="item.selected"
      @selected="onSelect"
    />
  </div>
</template>

<script>
import ListItem from './ListItem.vue';
export default {
  name: 'List',
  components: {
    ListItem,
  },
  props: {
    listItems: {
      type: Array,
      required: true,
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
.title {
  color: #6a6a6a;
  font-size: 16px;
}
</style>