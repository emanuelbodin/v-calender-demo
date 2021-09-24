<template>
  <div class="tab">
    <div class="tab-container">
      <div class="tab-title">2021</div>
      <div v-for="tabItem in tabs" :key="tabItem.label" class="tab-item">
        {{ tabItem.label }}
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
          label: 'Jan',
        },
        {
          label: 'Feb',
        },
        {
          label: 'Mar',
        },
        {
          label: 'Apr',
        },
        {
          label: 'Maj',
        },
        {
          label: 'Jun',
        },
        {
          label: 'Jul',
        },
        {
          label: 'Aug',
        },
        {
          label: 'Sep',
        },
        {
          label: 'Okt',
        },
        {
          label: 'Nov',
        },
        {
          label: 'Dec',
        },
      ],
    };
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

.tab-item:last-child {
  margin-bottom: 10px;
}
</style>