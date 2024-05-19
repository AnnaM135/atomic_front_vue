<template>
  <div class="dropdown-with-label">
    <label :for="id">{{ label }}</label>
    <Dropdown :placeholder="placeholder">
      <template v-slot>
        <div 
          class="option" 
          v-for="(option, index) in options" 
          :key="index" 
          @click="selectOption(option)">
          {{ option }}
        </div>
      </template>
    </Dropdown>
  </div>
</template>

<script>
import {Dropdown} from '@/components/atoms';

export default {
  components: {
    Dropdown
  },
  props: {
    id: String,
    label: String,
    options: Array,
    placeholder: String
  },
  methods: {
    selectOption(option) {
      this.$emit('input', option);
    }
  }
};
</script>


<style scoped>
.dropdown-with-label {
  display: flex;
  flex-direction: column;
  row-gap: 5px;
}

label {
  font-size: 14px;
  color: #333;
}
</style>
