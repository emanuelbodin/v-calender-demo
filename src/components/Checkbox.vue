<template>
  <div class="checkbox">
    <label class="item">
      <label :for="id" class="checkbox__label" />
      <input :id="id" v-model="checkboxValue" type="checkbox" hidden />
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
  data() {
    return {
      checkboxValue: true,
    };
  },
  computed: {
    style() {
      if (this.checked) {
        return {
          opacity: 1,
          transform: 'translate(-50%, -50%) rotateZ(40deg) scale(1)',
        };
      } else {
        return {};
      }
    },
  },
  watch: {
    checkboxValue(value) {
      this.$emit('toggle', value, this.id);
    },
    checked() {
      this.checkboxValue = this.checked;
    },
  },
  created() {
    if (this.checkboxValue !== this.checked) this.checkboxValue = this.checked;
  },
};
</script>

<style scoped>
.checkbox {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.checkbox .checkmark {
  display: block;
  width: 20px;
  height: 20px;
  background-color: #fff;
  border-radius: 5px;
  position: relative;
  transition: background-color 0.4s;
  cursor: pointer;
  border: 1px solid #6a6a6a;
}

.checkbox .checkmark:after {
  content: '';
  position: absolute;
  width: 6px;
  height: 9px;
  border-right: 3px solid #fff;
  border-bottom: 3px solid #fff;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) rotateZ(40deg) scale(5);
  transition: all 0.4s;
  opacity: 0;
}

.checkbox input:checked ~ .checkmark:after {
  opacity: 1;
  transform: translate(-50%, -50%) rotateZ(40deg) scale(1);
}

.checkbox input:checked ~ .checkmark {
  background-color: #6a6a6a;
}
</style>
