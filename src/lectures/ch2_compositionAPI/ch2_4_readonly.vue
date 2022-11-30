<template>
  <div></div>
</template>

<script>
import { reactive, readonly } from 'vue';

export default {
  setup() {
    const original = reactive({
      count: 0,
    });
    const copy = readonly(original);
    original.count++;
    copy.count++; // readonly이기 때문에 쓰기동작이 되지 않음
    console.log(original.count);
    console.log(copy.count);
    return {};
  },
};
</script>

<style lang="scss" scoped>

</style>