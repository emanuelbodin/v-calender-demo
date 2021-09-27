<template>
  <div class="container">
    <div class="tabs">
      <div
        v-for="option in tabOptions"
        :key="option.title"
        class="tab-item"
        :class="{ active: option.active }"
        @click="selectTab(option)"
      >
        {{ option.title }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tabs',
  props: {
    tabOptions: {
      type: Array,
      required: true,
    },
  },
  methods: {
    selectTab(option) {
      if (option.active) return;
      this.selectedTab = option.value;
      this.$emit('changeTab', option.value);
    },
  },
};
</script>

<style scoped>
.container {
  margin-bottom: 20px;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  border-radius: 4px;
}

.tabs {
  width: 100%;
  background-color: #efefef;
  border-radius: 8px;
  cursor: pointer;
  display: flex;
}

.tab-item {
  flex-grow: 1;
  padding-top: 3px;
  padding-bottom: 4px;
  border: 2px solid #efefef;
  border-radius: 4px;
  color: #949494;
  user-select: none;
  text-align: center;
  transition: 0.3s ease-in-out;
  border-left: 1px solid #cccccc;
}

.active {
  background-color: #6a6a6a;
  color: #f8f8f8;
  border: 2px solid #707070;
  box-shadow: 0 1px 6px rgba(0, 0, 0, 0.25);
  border-radius: 8px;
  font-weight: normal;
}
</style>
