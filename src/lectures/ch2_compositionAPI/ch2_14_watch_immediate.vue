<template>
  <div>
    <p>{{ message }}</p>
    <p>{{ reverseMessage }}</p>
  </div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  setup() {
    const message = ref('Hello Vue3');
    const reverseMessage = ref('');

    const reverseFunction = newValue => {
      console.log('즉시실행함!!!');
      reverseMessage.value = newValue.split('').reverse().join('');
    };

    watch(message, reverseFunction,
      {
        immediate: true, // 선언시 바로 실행하기 원하면 이걸 붙혀주자
      },
    );
    return { message, reverseMessage };
  },
};
</script>

<style scoped>

</style>