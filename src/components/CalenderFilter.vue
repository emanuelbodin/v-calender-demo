<template>
  <div>
    <div class="tabContainer">
      <Tabs :tabOptions="tabOptions" @changeTab="changeTab" />
    </div>
    <div class="checkbox-row">
      <div
        v-for="item in checkboxOptions"
        :key="item.id"
        class="checkbox-container"
      >
        <div class="center">
          <Checkbox :id="item.id" :checked="item.checked" />
        </div>
        <div>
          <div class="checkbox-title">{{ item.title }}</div>
          <div class="checkboxSubtitle">{{ item.subtitle }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Tabs from './Tabs.vue';
import Checkbox from './Checkbox.vue';
export default {
  name: 'CalenderFilter',
  components: {
    Tabs,
    Checkbox,
  },
  props: {
    tabOptions: {
      type: Array,
      required: true,
    },
    checkboxOptions: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {
    changeTab(value) {
      this.$emit('changeTab', value);
    },
  },
};
</script>

<style scoped>
.tabContainer {
  width: 100%;
}

.checkbox-row {
  display: flex;
  width: 100%;
  justify-content: space-around;
}

.checkbox-container {
  display: flex;
}

.center {
  align-self: flex-start;
}

.checkbox-title {
  margin-left: 5px;
  font-family: Raleway;
  font-size: 15px;
  color: #6a6a6a;
}

.checkboxSubtitle {
  margin-left: 5px;
  font-family: Raleway;
  font-size: 14px;
  color: #6a6a6a;
}
</style>