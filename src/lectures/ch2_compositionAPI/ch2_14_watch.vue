<template>
  <div></div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  setup() {
    const message = ref('');

    // watch(감시값, 반응함수): 값을 감시하고 바뀔때마다 반응하기
    watch(message, (newValue, oldValue) => {
      console.log('newValue: ', newValue);
      console.log('oldValue: ', oldValue);
    });

    return {
      message,
    };
  },
};
</script>

<style scoped>

</style>