<template>
  <div>
    <List :listItems="choices" @selected="onSelect" />
  </div>
</template>

<script>
import List from './List';
const monthNames = [
  'Jan',
  'Feb',
  'Mar',
  'Apr',
  'Maj',
  'Jun',
  'Jul',
  'Aug',
  'Sep',
  'Okt',
  'Nov',
  'Dec',
];
export default {
  name: 'QuickChoices',
  components: {
    List,
  },
  props: {
    shouldClear: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
      choices: null,
    };
  },
  watch: {
    shouldClear() {
      this.choices = this.choices.map((el) => {
        el.selected = false;
        return el;
      });
    },
  },
  created() {
    this.setChoices();
  },
  methods: {
    onSelect(id) {
      this.choices = this.choices.map((el) => {
        if (el.id === id) el.selected = true;
        else el.selected = false;
        return el;
      });
      const choice = this.choices.find((el) => el.id === id);
      if (id != null) this.$emit('select', choice.start, choice.end, false);
    },
    getDaysInMonth(date) {
      return new Date(date.getFullYear(), date.getMonth() + 1, 0).getDate();
    },
    setChoices() {
      const today = new Date();
      const yesterday = new Date(new Date().setDate(today.getDate() - 1));
      const prevMonday = new Date(new Date().setDate(today.getDate() - 7));
      prevMonday.setDate(
        prevMonday.getDate() - Math.abs((today.getDay() + 6) % 7)
      );
      const prevSunday = new Date(new Date().setDate(prevMonday.getDate() + 6));
      const lastWeekString =
        monthNames[prevMonday.getMonth()] === monthNames[prevSunday.getMonth()]
          ? `${
              monthNames[prevMonday.getMonth()]
            } ${prevMonday.getDate()}-${prevSunday.getDate()}`
          : `${monthNames[prevMonday.getMonth()]} ${prevMonday.getDate()}-${
              monthNames[prevMonday.getMonth()]
            } ${prevSunday.getDate()}`;
      const startLastMonth = new Date(
        today.getFullYear(),
        today.getMonth() - 1,
        1
      );
      const endLastMonth = new Date(today.getFullYear(), today.getMonth(), 0);
      const daysInLastMonth = this.getDaysInMonth(startLastMonth);
      const quarter = Math.floor(today.getMonth() / 3);
      const startFullQuarter = new Date(
        today.getFullYear(),
        quarter * 3 - 3,
        1
      );
      const endFullQuarter = new Date(
        startFullQuarter.getFullYear(),
        startFullQuarter.getMonth() + 3,
        0
      );
      this.choices = [
        {
          id: 'choice_1',
          title: 'Idag',
          value: `${monthNames[today.getMonth()]} ${today.getDate()}`,
          selected: false,
          start: today,
          end: today,
        },
        {
          id: 'choice_2',
          title: 'Igår',
          value: `${monthNames[yesterday.getMonth()]} ${yesterday.getDate()}`,
          selected: false,
          start: yesterday,
          end: yesterday,
        },
        {
          id: 'choice_3',
          title: 'Förra veckan',
          value: lastWeekString,
          selected: false,
          start: prevMonday,
          end: prevSunday,
        },
        {
          id: 'choice_4',
          title: 'Förra månaden',
          value: `1-${daysInLastMonth} ${
            monthNames[startLastMonth.getMonth()]
          }`,
          selected: false,
          start: startLastMonth,
          end: endLastMonth,
        },
        {
          id: 'choice_5',
          title: 'Förra kvartalet',
          value: `${startFullQuarter.getDate()} ${
            monthNames[startFullQuarter.getMonth()]
          } - ${endFullQuarter.getDate()} ${
            monthNames[endFullQuarter.getMonth()]
          }`,
          selected: false,
          start: startFullQuarter,
          end: endFullQuarter,
        },
      ];
    },
  },
};
</script>

<style scoped>
</style>