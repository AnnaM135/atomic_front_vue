<template>
  <BaseToggle :initialActive="initialActive" v-slot="{ active, toggle }">
    <div class="icon-toggle">
      <button
        v-for="(icon, index) in icons"
        :key="index"
        :class="{ active: active === index }"
        @click="toggle(index)"
        class="button icon"
      >
        <img :src="icon" alt="Icon" />
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
    icons: {
      type: Array,
      required: true
    }
  }
};
</script>

<style lang="scss" scoped>
@import '@/styles/index.scss';
.icon-toggle {
    width: max-content;
    display: flex;
}
.icon {
    width: 36px;
    height: 36px;
    border: 1px solid $blue-50;
    background: transparent;
    transition: .5s ease;
    &:first-child {
        border-radius: 6px 0px 0px 6px;
    }
    &:last-child {
        border-radius: 0px 6px 6px 0px;
        border-left: none;
    }
}


.icon.active {
    background: $blue-50;
}
</style>
