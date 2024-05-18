<template>
  <div
    :class="[
      'checkbox',
      { 'checkbox--checked': isChecked },
      { 'checkbox--intermediate': isIntermediate },
      { 'checkbox--disabled': isDisabled }
    ]"
    @click="toggleCheck"
  >
  </div>
</template>

<script>
export default {
  name: 'Checkbox',
  props: {
    value: Boolean,
    intermediate: Boolean,
    disabled: Boolean,
  },
  data() {
    return {
      isChecked: this.value,
      isIntermediate: this.intermediate,
      isDisabled: this.disabled
    };
  },
  methods: {
    toggleCheck() {
      if(this.intermediate) return
      if (!this.isDisabled) {
        this.isChecked = !this.isChecked;
        this.$emit('input', this.isChecked);
      }
    },
  },
  watch: {
    value(newVal) {
      this.isChecked = newVal;
    },
    intermediate(newVal) {
      this.isIntermediate = newVal;
    },
    disabled(newVal) {
      this.isDisabled = newVal;
    },
  },
};
</script>

<style lang="scss" scoped>
@import '@/styles/index.scss';
</style>
