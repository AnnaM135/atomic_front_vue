<template>
  <BaseToggle :initialActive="initialActive" v-slot="{ active, toggle }">
    <div class="text-toggle">
      <button
        v-for="(label, index) in labels"
        :key="index"
        :class="{ active: active === index }"
        @click="toggle(index)"
        class="button text-button"
      >
        {{ label }}
      </button>
    </div>
      <div class="content">
        <slot :name="'content-' + active"></slot>
      </div>
  </BaseToggle>
</template>

<script>
import BaseToggle from '../common/BaseToggle.vue';

export default {
  components: {
    BaseToggle
  },
  props: {
    initialActive: {
      type: Number,
      default: 0
    },
    labels: {
      type: Array,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
@import '@/styles/index.scss';
.text-toggle {
    width: max-content;
    display: flex;
}

.text-button {
    flex: 1;
    min-width: 112px;
    padding: 10px 16px;
    border: 1px solid $blue-50;
    background: transparent;
    color: $blue-100;
    transition: .5s ease;
    &:first-child {
        border-radius: 8px 0px 0px 8px;
    }
    &:last-child {
        border-radius: 0px 8px 8px 0px;
        border-left: none;
    }
}

.text-button.active {
  background: $blue-500;
  color: white;
}
</style>
