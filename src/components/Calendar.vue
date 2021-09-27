<template>
  <div class="container">
    <v-calendar
      :is-expanded="true"
      show-weeknumbers
      :attributes="attributes"
      :theme="themeStyles"
      @dayclick="onDayClick"
    >
      >
      <span slot="header-title" />
      <span slot="header-left-button" />
      <span slot="header-right-button" />
    </v-calendar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      start: new Date(),
      end: null,
      themeStyles: {
        contanier: {
          background: 'linear-gradient(to bottom right, #ff5050, #ff66b3)',
          color: '#fafafa',
        },
      },
    };
  },
  computed: {
    attributes() {
      if (this.start == null) return;
      const dates = {
        start: this.start,
        end: this.end == null ? this.start : this.end,
      };
      return [
        {
          highlight: {
            start: {
              fillMode: 'solid',
              style: {
                background: '#6A6A6A',
              },
              contentStyle: {
                color: 'white',
              },
            },
            base: {
              fillMode: 'light',
              style: {
                background: '#EFEFEF',
              },
            },
            end: {
              fillMode: 'solid',
              style: {
                background: '#6A6A6A',
              },
              contentStyle: {
                color: 'white',
              },
            },
          },
          dates,
        },
      ];
    },
  },
  methods: {
    onDayClick(day) {
      const date = new Date(day.id);
      if (this.end != null) {
        this.start = date;
        this.end = null;
        return;
      } else if (date < this.start) {
        this.end = this.start;
        this.start = date;
        return;
      }
      this.end = date;
    },
  },
};
</script>

<style scoped>
.container {
}
</style>
