<template>
  <div>
    <List :listItems="choices" @selected="onSelect" />
  </div>
</template>

<script>
import List from './List';
export default {
  name: 'QuickChoices',
  components: {
    List,
  },
  data() {
    return {
      choices: [
        {
          id: 'choice_1',
          title: 'Idag',
          value: 'Sep 15',
          selected: false,
        },
        {
          id: 'choice_2',
          title: 'Igår',
          value: 'Sep 14',
          selected: false,
        },
        {
          id: 'choice_3',
          title: 'Förra veckan',
          value: 'Sep 6-10',
          selected: false,
        },
        {
          id: 'choice_4',
          title: 'Förra månaden',
          value: 'Aig 1-31',
          selected: false,
        },
        {
          id: 'choice_5',
          title: 'Förra kvartalet',
          value: '1 juli till och med 30 september',
          selected: false,
        },
      ],
    };
  },
  methods: {
    onSelect(id) {
      this.choices = this.choices.map((el) => {
        if (el.id === id) el.selected = true;
        else el.selected = false;
        return el;
      });
    },
  },
};
</script>

<style scoped>
</style>