<template>
  <component
    :is="elementType"
    :id="id"
    :value="value"
    :placeholder="placeholder"
    :disabled="disabled"
    :class="[
      'input',
      {
        'filled': filled,
        'error': error,
        'disabled': disabled,
      },
      size
    ]"
    @input="handleInput"
    @focus="handleFocus"
    @blur="handleBlur"
    :type="type"
    :rows="rows"
    :cols="cols"
  />
</template>

<script>
export default {
  props: {
    id: String,
    type: String,
    value: String,
    placeholder: String,
    required: Boolean,
    disabled: Boolean,
    filled: Boolean,
    error: Boolean,
    size: String,
    rows: String,
    cols: String,
    elementType: {
      type: String,
      default: 'input'
    }
  },
  methods: {
    handleInput(event) {
      // Handle input event
    },
    handleFocus(event) {
      // Handle focus event
    },
    handleBlur(event) {
      // Handle blur event
    }
  }
};
</script>

<style lang="scss" scoped>
@import '@/styles/index.scss';
</style>
