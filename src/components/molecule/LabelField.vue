<template>
  <div class="label-field">
    <label class="label-field-text" :for="id" v-if="label">
        {{ label }}
        <span v-if="required" class="required-asterisk">*</span>
    </label>
    <BaseInput
      :id="id"
      :value="defaultValue"
      :placeholder="placeholder"
      :disabled="disabled"
      :error="error"
      :required="required"
      :type="type"
      :size="size"
    />
    <!-- <div class="alert-message" v-if="alertMessage">{{ alertMessage }}</div>
    <div class="helper-text" v-if="helperText">{{ helperText }}</div> -->
  </div>
</template>

<script>
import { BaseInput } from '@/components/atoms';

export default {
  components: {
    BaseInput
  },
  props: {
    id: String,
    label: String,
    defaultValue: {
      type: [String, Number],
      default: ''
    },
    placeholder: String,
    disabled: Boolean,
    required: Boolean,
    error: Boolean,
    type: {
      type: String,
      default: 'text'
    },
    helperText: String,
    alertMessage: String,
    size: String,
    rows: String
  }
};
</script>


