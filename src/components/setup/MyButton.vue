<template>
  <div class="p-3 bg-danger">
    <button class="btn btn-primary" type="button" v-bind="$attrs">
      My Button {{ message }}
    </button>
  </div>
</template>

<script>
export default {
  inheritAttrs: false, // 속성 자동 상속 봉인!
}
</script>
<script setup>
import { ref } from 'vue';
const message = ref('message');
</script>

<style scoped>

</style>