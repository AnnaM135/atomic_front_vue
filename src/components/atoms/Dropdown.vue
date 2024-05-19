<template>
  <div class="base-dropdown" @click="toggleDropdown">
    <div class="select-container">
      <span>{{ displayText }}</span>
      <span class="arrow"></span>
    </div>
    <div class="options" v-if="isOpen">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    placeholder: {
      type: String,
      default: 'Select...'
    }
  },
  data() {
    return {
      isOpen: false,
      selectedOption: null
    };
  },
  computed: {
    displayText() {
      return this.selectedOption || this.placeholder;
    }
  },
  methods: {
    toggleDropdown() {
      this.isOpen = !this.isOpen;
    },
    selectOption(option) {
      this.selectedOption = option;
      this.isOpen = false;
      this.$emit('input', option);
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
  }
};
</script>


<style scoped>
.dropdown {
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
  padding: 10px;
  cursor: pointer;
}

.option:hover {
  background: #eee;
}
</style>
