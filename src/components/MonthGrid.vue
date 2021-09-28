<template>
  <div class="container">
    <div
      v-for="month in monthList"
      :key="month.id"
      class="item"
      :class="{ selected: month.selected }"
      @click="onSelect(month.id)"
    >
      {{ month.label }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'MonthGrid',
  components: {},
  props: {},
  data() {
    return {
      monthList: [
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
      this.monthList = this.monthList.map((el) => {
        if (el.id === id) el.selected = !el.selected;
        return el;
      });
    },
  },
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
}

.item {
  color: #6a6a6a;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
  padding: 5px;
  text-align: center;
  cursor: pointer;
}

.selected,
.item:hover {
  color: white;
  background-color: #6a6a6a;
}
</style>