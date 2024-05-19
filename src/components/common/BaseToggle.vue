<template>
  <div>
    <slot :active="active" :toggle="toggle"></slot>
  </div>
</template>

<script>
export default {
  props: {
    initialActive: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      active: this.initialActive
    };
  },
  methods: {
    toggle(index) {
      this.active = index;
    }
  }
};
</script>
