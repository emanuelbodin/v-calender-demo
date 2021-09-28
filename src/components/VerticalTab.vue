<template>
  <div class="tab">
    <div class="tab-container">
      <div v-if="timeSetting === 'MONTH'" class="tab-title">
        {{ currentYear }}
      </div>
      <div
        v-for="tabItem in tabs"
        :key="tabItem.label"
        class="tab-item"
        :class="{ notSelectable: !tabItem.selectable }"
        @click="onSelect(tabItem.id, tabItem.selectable)"
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
  props: {
    timeSetting: {
      type: String,
      required: true,
    },
    selectedMonth: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      currentYear: null,
      months: [
        {
          id: '1',
          label: 'Jan',
          selected: false,
          selectable: false,
        },
        {
          id: '2',
          label: 'Feb',
          selected: false,
          selectable: false,
        },
        {
          id: '3',
          label: 'Mar',
          selected: false,
          selectable: false,
        },
        {
          id: '4',
          label: 'Apr',
          selected: false,
          selectable: false,
        },
        {
          id: '5',
          label: 'Maj',
          selected: false,
          selectable: false,
        },
        {
          id: '6',
          label: 'Jun',
          selected: false,
          selectable: false,
        },
        {
          id: '7',
          label: 'Jul',
          selected: false,
          selectable: false,
        },
        {
          id: '8',
          label: 'Aug',
          selected: false,
          selectable: false,
        },
        {
          id: '9',
          label: 'Sep',
          selected: false,
          selectable: false,
        },
        {
          id: '10',
          label: 'Okt',
          selected: false,
          selectable: false,
        },
        {
          id: '11',
          label: 'Nov',
          selected: false,
          selectable: false,
        },
        {
          id: '12',
          label: 'Dec',
          selected: false,
          selectable: false,
        },
      ],
      years: [
        { id: '2019', label: '2019', selected: false, selectable: true },
        { id: '2020', label: '2020', selected: false, selectable: true },
        { id: '2021', label: '2021', selected: false, selectable: true },
      ],
    };
  },
  computed: {
    tabs() {
      if (this.timeSetting === 'MONTH') return this.months;
      else return this.years;
    },
  },
  watch: {
    selectedMonth() {
      this.months = this.months.filter((el) => {
        if (el.id == this.selectedMonth) el.selected = true;
        else el.selected = false;
        return el;
      });
    },
  },
  created() {
    const date = new Date();
    const currentYear = date.getFullYear();
    const currentMonth = date.getMonth() + 1;
    this.years = this.years.map((el) => {
      const id = parseInt(el.id);
      if (id == currentYear) el.selected = true;
      return el;
    });
    this.months = this.months.map((el) => {
      const id = parseInt(el.id);
      if (id === currentMonth) el.selected = true;
      if (id <= currentMonth) el.selectable = true;
      return el;
    });
  },
  methods: {
    onSelect(id, selectable) {
      if (!selectable) return;
      if (this.timeSetting === 'MONTH') {
        this.months = this.months.filter((el) => {
          if (el.id === id) el.selected = true;
          else el.selected = false;
          return el;
        });
        this.$emit('timeChange', 'MONTH', id);
      } else {
        this.years = this.years.filter((el) => {
          if (el.id === id) el.selected = true;
          else el.selected = false;
          return el;
        });
        this.$emit('timeChange', 'YEAR', id);
      }
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
  justify-content: center;
  align-items: center;
  gap: 10px;
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

.tab-item:hover {
  color: rgba(248, 248, 248, 0.5);
}

.tab-item:last-child {
  margin-bottom: 10px;
}

.arrowContainer {
  position: absolute;
  right: -1px;
}

.notSelectable {
  color: rgba(248, 248, 248, 0.5);
  cursor: not-allowed;
}
</style>