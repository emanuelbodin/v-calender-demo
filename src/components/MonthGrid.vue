<template>
  <div class="container">
    <div
      v-for="month in monthList"
      :key="month.id"
      class="item"
      :class="{ selected: month.selected, hovered: month.hovered }"
      @click="onSelect(month.id)"
      @mouseover="onHover(month.id)"
      @mouseleave="onHoverLeave()"
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
      start: null,
      end: null,
      monthList: [
        {
          id: 0,
          label: 'Jan',
          selected: false,
          hovered: false,
        },
        {
          id: 1,
          label: 'Feb',
          selected: false,
          hovered: false,
        },
        {
          id: 2,
          label: 'Mar',
          selected: false,
          hovered: false,
        },
        {
          id: 3,
          label: 'Apr',
          selected: false,
          hovered: false,
        },
        {
          id: 4,
          label: 'Maj',
          selected: false,
          hovered: false,
        },
        {
          id: 5,
          label: 'Jun',
          selected: false,
          hovered: false,
        },
        {
          id: 6,
          label: 'Jul',
          selected: false,
          hovered: false,
        },
        {
          id: 7,
          label: 'Aug',
          selected: false,
          hovered: false,
        },
        {
          id: 8,
          label: 'Sep',
          selected: false,
          hovered: false,
        },
        {
          id: 9,
          label: 'Okt',
          selected: false,
          hovered: false,
        },
        {
          id: 10,
          label: 'Nov',
          selected: false,
          hovered: false,
        },
        {
          id: 11,
          label: 'Dec',
          selected: false,
          hovered: false,
        },
      ],
    };
  },
  methods: {
    onSelect(id) {
      if (this.start != null && this.end != null) {
        this.start = null;
        this.end = null;
        this.monthList = this.monthList.map((el) => {
          el.selected = false;
          return el;
        });
      } else if (this.start == null) {
        this.start = id;
        this.monthList = this.monthList.map((el) => {
          if (el.id === this.start) el.selected = true;
          return el;
        });
      } else {
        this.end = id;
        const startIndex = this.monthList.findIndex(
          (el) => el.id === this.start
        );
        const endIndex = this.monthList.findIndex((el) => el.id === this.end);
        this.monthList = this.monthList.map((el, index) => {
          if (index >= startIndex && index <= endIndex) el.selected = true;
          return el;
        });
        this.$emit('monthChange');
      }
    },
    onHover(id) {
      if (this.start == null || (this.start != null && this.end != null))
        return;
      const startIndex = this.monthList.findIndex((el) => el.id === this.start);
      const foundIndex = this.monthList.findIndex((el) => el.id === id);
      this.monthList = this.monthList.map((el, index) => {
        if (index >= startIndex && index <= foundIndex) el.hovered = true;
        return el;
      });
    },
    onHoverLeave() {
      this.monthList = this.monthList.map((el) => {
        el.hovered = false;
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
.item:hover,
.hovered {
  color: white;
  background-color: #6a6a6a;
}
</style>