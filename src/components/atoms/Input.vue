<template>
  <input
    :id="id"
    :value="value"
    :placeholder="placeholder"
    :disabled="disabled"
    :class="[
      'input',
      {
        'filled': filled,
        'error': error,
        'disabled': disabled
      },
      size
    ]"
    @input="handleInput"
    @focus="handleFocus"
    @blur="handleBlur"
    :type="type"
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
    size: String
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