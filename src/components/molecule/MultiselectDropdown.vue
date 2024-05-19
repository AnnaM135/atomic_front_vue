<template>
  <div class="multiselect-dropdown" @click="toggleDropdown">
    <div class="select-container">
      <span>{{ selectedOptions.length ? selectedOptions.join(', ') : placeholder }}</span>
      <span class="arrow"></span>
    </div>
    <div class="options" v-if="isOpen">
      <div 
        class="option" 
        v-for="(option, index) in options" 
        :key="index"
        @click="selectOption(option)">
        <input 
          type="checkbox" 
          :id="`checkbox-${index}`" 
          :value="option" 
          v-model="selectedOptions"
          @click.stop /> <!-- Stop click event propagation -->
        <label :for="`checkbox-${index}`" @click.stop>{{ option }}</label> <!-- Stop click event propagation -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      required: true
    },
    placeholder: {
      type: String,
      default: 'Select...'
    }
  },
  data() {
    return {
      isOpen: false,
      selectedOptions: []
    };
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    handleClickOutside(event) {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    }
  },
  mounted() {
    document.addEventListener('click', this.handleClickOutside);
  },
  beforeDestroy() {
    document.removeEventListener('click', this.handleClickOutside);
  },
  watch: {
    selectedOptions(newVal) {
      this.$emit('input', newVal);
    }
  }
};
</script>

<style scoped>
.multiselect-dropdown {
  position: relative;
  display: inline-block;
  width: 200px;
}

.select-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border: 1px solid #ccc;
  cursor: pointer;
}

.arrow {
  width: 0; 
  height: 0; 
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid #000;
}

.options {
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  border: 1px solid #ccc;
  background: #fff;
  z-index: 1000;
}

.option {
  display: flex;
  align-items: center;
  padding: 10px;
}

.option:hover {
  background: #eee;
}
</style>
