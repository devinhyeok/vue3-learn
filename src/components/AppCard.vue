<template>
  <div class="card">
    <div v-if="$slots.header" class="card-header">
      <slot name="header" header-message="header message"></slot>
    </div>
    <div v-if="$slots.default" class="card-body">
      <slot :child-message="childMessage" hello-message="hello from parent"></slot>
    </div>
    <div v-if="hasFooter" class="card-footer text-muted">
      <slot name="footer" footer-message="footer message"></slot>
    </div>
  </div>
</template>

<script>
import { computed } from '@vue/reactivity';
import { ref } from 'vue';

export default {
  setup(props, { slots }) {
    const childMessage = ref("child component message");
    // context.slots
    const hasFooter = computed(() => !!slots.footer);
    return { childMessage, hasFooter };
  },
};
</script>

<style scoped>

</style>