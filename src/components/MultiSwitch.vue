<template>
  <div class="navigation-multi-switch">
    <div v-show="isOpen" class="content">
      <slot />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MultiSwitch',
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      isOpen: true,
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.navigation-multi-switch {
  background-color: #efefef;
  border-radius: 8px;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  min-width: 120px;
}

.heading {
  margin-left: 10px;
  padding-right: 2px;
  padding-top: 1px;
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}

.content {
  border-radius: 8px;
  display: flex;
  overflow: scroll;
  width: 100%;
}
.content::-webkit-scrollbar {
  display: none;
}
</style>
