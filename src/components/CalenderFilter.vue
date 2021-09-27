<template>
  <div>
    <div class="tabContainer">
      <Tabs :tabOptions="tabOptions" @changeTab="changeTimeSetting" />
    </div>
    <div class="checkbox-row">
      <div
        v-for="item in checkboxOptions"
        :key="item.id"
        class="checkbox-container"
      >
        <Checkbox :id="item.id" :checked="item.checked" />
        <p class="checkbox-title">{{ item.title }}</p>
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
  data() {
    return {
      tabOptions: [
        { title: 'Månad', value: 'MONTH', active: true },
        { title: 'År', value: 'YEAR', active: false },
      ],
      checkboxOptions: [
        { id: 'workDays', checked: true, title: 'Endast Arbetsdagar Mån-Fre' },
        { id: 'workTime', checked: true, title: 'Endast Arbetstid 8:00-17:00' },
      ],
    };
  },
  methods: {
    changeTimeSetting(value) {
      this.tabOptions.map((el) => {
        if (el.value === value) el.active = true;
        else el.active = false;
        return el;
      });
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

.checkbox-title {
  align-self: center;
  margin-left: 3px;
  font-family: Raleway;
  font-size: 15px;
  color: #6a6a6a;
}
</style>