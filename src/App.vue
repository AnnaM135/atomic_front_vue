<script>
import { Checkbox } from '@/components/atoms';
export default {
  components: {
    Checkbox,
  },
  data() {
    return {
      isChecked: false,
    };
  },
};
</script>

<template>
  <div>
    <h1>Atomic Frontend</h1>
    <button class="button">button</button>
    <div class="checkbox-container">
      <div class="checkbox-column">Default: <Checkbox v-model="isChecked" /></div>
      <div class="checkbox-column">Checked: <Checkbox v-model="isChecked" class="checkbox--checked" /></div>
      <div class="checkbox-column">Interminate: <Checkbox v-model="isChecked" intermediate /></div>
      <div class="checkbox-column">Interminate Disable: <Checkbox v-model="isChecked" intermediate :disabled="true" /></div>
      <div class="checkbox-column">Disable: <Checkbox v-model="isChecked" :disabled="true" /></div>
    </div>
  </div>

</template>

<style scoped>
.checkbox-container {
    margin-top: 30px;
    border: 1px dotted;
    max-width: max-content;
    display: flex;
    flex-wrap: wrap;
    column-gap: 30px;
    padding: 10px 30px;
}
.checkbox-column {
    display: flex;
    align-items: center;
    column-gap: 10px;
}
</style>
