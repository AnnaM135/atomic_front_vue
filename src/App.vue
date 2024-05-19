<script>
import { Checkbox } from '@/components/atoms';
import { Input } from '@/components/atoms';
import { LabelField } from "@/components/molecule";
import { BaseInput } from "@/components/atoms";
import { IconToggleMenu } from '@/components/atoms';
import { ToggleMenu } from '@/components/atoms';

export default {
  components: {
    Checkbox,
    LabelField,
    Input,
    BaseInput,
    ToggleMenu,
    IconToggleMenu
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
    <div class="form">
      <div class="input-container">
                <div class="input-column">Default Small:<BaseInput elementType="textarea" type="text" size="lg" rows="4" cols="50" placeholder="Placeholder"/></div>

        <div class="input-column">Default Small:<BaseInput elementType="input" type="text" size="sm" placeholder="Placeholder"/></div>
        <div class="input-column">Default Big: <BaseInput type="text" size="lg" /></div>
        <div class="input-column">Error: <BaseInput type="email" size="lg" value="Value" error/></div>
        <div class="input-column">Disable: <BaseInput type="text" size="lg" disabled value="Value"/></div>
      </div>
      <div class="form-label">
        <LabelField
          id="outlined-error-helper-text"
          label="Enter your name"
          defaultValue="Hello World"
          helperText="Incorrect entry."
          alertMessage="Error: Incorrect entry."
          type="text"
          size="lg"
        />
      <LabelField
        id="outlined-disabled-helper-text"
        label="Disabled field"
        defaultValue="Hello World"
        disabled
        type="text"
        size="lg"
      />
      <LabelField
        id="outlined-required"
        label="Required field"
        required
        type="text"
        size="lg"
      />
      </div>
    </div>
    <div class="toggle-menu">
      <IconToggleMenu :icons="['/path/to/icon1.svg', '/path/to/icon2.svg']">
        <template #content-0>
          <p>Content for icon 1</p>
        </template>
        <template #content-1>
          <p>Content for icon 2</p>
        </template>
      </IconToggleMenu>

      <ToggleMenu :labels="['By category', 'All products']">
        <template #content-0>
          <p>Content for option 1</p>
        </template>
        <template #content-1>
          <p>Content for option 2</p>
        </template>
      </ToggleMenu>
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
.input-container {
    display: flex;
    flex-direction: column;
    row-gap: 20px;
}
.input-column {
  width: 300px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.form {
  display: flex;
  column-gap: 50px;
}
.form-label {
  display: flex;
  flex-direction: column;
  row-gap: 20px;
}
.toggle-menu {
  border: 1px dotted;
  padding: 10px 30px;
  margin-block: 30px;
  width: 400px;
}
</style>
