<template>
  <div class="checkbox">
    <label class="item">
      <label :for="id" class="checkbox__label" />
      <input
        :id="id"
        :checked="checked"
        type="checkbox"
        hidden
        @click="onToggle"
      />
      <span :for="id" class="checkmark" />
    </label>
  </div>
</template>

<script>
export default {
  name: 'Checkbox',
  props: {
    id: {
      type: [Number, String],
      required: true,
    },
    checked: {
      type: Boolean,
      required: true,
    },
  },
  methods: {
    onToggle() {
      this.$emit('toggle', this.id);
    },
  },
};
</script>

<style scoped>
.checkbox {
  width: 100%;
  height: 100%;
}

.checkbox .checkmark {
  display: block;
  width: 100%;
  height: 100%;
  background: #f8f8f8;
  border-radius: 2px;
  position: relative;
  transition: background-color 0.4s;
  cursor: pointer;
  border: 0.5px solid #f8f8f8;
  box-shadow: inset 0px 0px 4px rgba(0, 0, 0, 0.25);
}

.checkbox .checkmark:after {
  content: '';
  position: absolute;
  width: 4px;
  height: 9px;
  border-right: 1.5px solid #6a6a6a;
  border-bottom: 1.5px solid #6a6a6a;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%) rotateZ(40deg) scale(4);
  transition: all 0.4s;
  opacity: 0;
}

.checkbox input:checked ~ .checkmark:after {
  opacity: 1;
  transform: translate(-50%, -50%) rotateZ(40deg) scale(1);
}

.checkbox input:checked ~ .checkmark {
  background-color: #f8f8f8;
}
</style>
