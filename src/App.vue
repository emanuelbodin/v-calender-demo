<template>
  <div
    class="app" 
    id="hej"
  >
    <button @click="openCalendar">
      Calendar
    </button>
    <calendar />
  </div>
</template>

<script>
import Calendar from "./components/Calendar.vue";

export default {
  name: "App",
  components: {
    Calendar,
  },
  data() {
    return {
      calendarVisible: false,
    };
  },
  methods: {
    openCalendar() {
      this.calendarVisible = true;
    },
  },
};
</script>

<style>
.app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
}
</style>
