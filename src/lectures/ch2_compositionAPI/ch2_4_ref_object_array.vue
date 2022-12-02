<template>
  <div></div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup() {
    // Object에서 ref 사용
    const count = ref(0);
    const state = reactive({
      count,
    });
    count.value++;
    console.log("state.count:", state.count); // 1

    // Array에서 ref 사용
    const message = ref('Hello');
    const arr = reactive([message]);
    console.log("arr[0].value:", arr[0].value); // Hello
    return {};
  },
};
</script>

<style lang="scss" scoped>

</style>