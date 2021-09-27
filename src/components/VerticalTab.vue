<template>
  <div class="tab">
    <div class="tab-container">
      <div class="tab-title">2021</div>
      <div
        v-for="tabItem in tabs"
        :key="tabItem.label"
        class="tab-item"
        @click="onSelect(tabItem.id)"
      >
        {{ tabItem.label }}
        <span v-if="tabItem.selected" class="arrowContainer">
          <img src="../assets/arrow.svg" />
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VerticalTab',
  data() {
    return {
      tabs: [
        {
          id: 'jan',
          label: 'Jan',
          selected: false,
        },
        {
          id: 'feb',
          label: 'Feb',
          selected: false,
        },
        {
          id: 'mar',
          label: 'Mar',
          selected: false,
        },
        {
          id: 'apr',
          label: 'Apr',
          selected: false,
        },
        {
          id: 'maj',
          label: 'Maj',
          selected: false,
        },
        {
          id: 'jun',
          label: 'Jun',
          selected: false,
        },
        {
          id: 'jul',
          label: 'Jul',
          selected: false,
        },
        {
          id: 'aug',
          label: 'Aug',
          selected: false,
        },
        {
          id: 'sep',
          label: 'Sep',
          selected: false,
        },
        {
          id: 'okt',
          label: 'Okt',
          selected: false,
        },
        {
          id: 'nov',
          label: 'Nov',
          selected: false,
        },
        {
          id: 'dec',
          label: 'Dec',
          selected: false,
        },
      ],
    };
  },
  methods: {
    onSelect(id) {
      this.tabs = this.tabs.filter((el) => {
        if (el.id === id) el.selected = true;
        else el.selected = false;
        return el;
      });
    },
  },
};
</script>

<style scoped>
.tab {
  height: 100%;
  width: 100%;
  background-color: #000;
  color: #fff;
}

.tab-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  height: 100%;
}

.tab-title {
  margin-top: 10px;
}

.tab-item {
  position: relative;
  width: 100%;
  text-align: center;
  cursor: pointer;
}

.tab-item:last-child {
  margin-bottom: 10px;
}

.arrowContainer {
  position: absolute;
  right: -1px;
}
</style>