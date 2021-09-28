<template>
  <div class="container">
    <v-calendar
      ref="calendar"
      :is-expanded="true"
      show-weeknumbers
      :attributes="attributes"
      @dayclick="onDayClick"
    >
      <span slot="header-title" />
      <span slot="header-left-button" />
      <span slot="header-right-button" />
    </v-calendar>
  </div>
</template>

<script>
export default {
  props: {
    start: {
      validator: (value) => typeof value === 'object' || value == null,
      required: true,
    },
    end: {
      validator: (value) => typeof value === 'object' || value == null,
      required: true,
    },
    selectedMonth: {
      type: Number,
      required: true,
    },
    selectedYear: {
      type: Number,
      required: true,
    },
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
  watch: {
    async selectedMonth() {
      await this.$refs.calendar.move({ month: this.selectedMonth, year: 2021 });
    },
  },
  methods: {
    onDayClick(day) {
      const date = new Date(day.id);
      let end;
      let start;
      if (this.end != null) {
        start = date;
        end = null;
      } else if (date < this.start) {
        end = this.start;
        start = date;
      } else {
        end = date;
        start = this.start;
      }
      this.$emit('dateChange', start, end);
    },
  },
};
</script>

<style scoped>
.container {
}
</style>
