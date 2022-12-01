<template>
  <div>
    <!--v-text, v-html-->
    <p>{{ msg }}</p>
    <p v-text="msg"></p>
    <p v-html="htmlStr"></p> <!--html로 인식-->
    <p v-text="htmlStr"></p> <!--text로 인식-->

    <!--v-pre: 요소내에 있는것을 그대로 렌더링합니다-->
    <p v-pre>{{msg 안녕하세요}}</p>

    <!--v-once: 한번만 렌더링함 값이 바뀌지 않음, 최적화용-->
    <p v-once>{{ msg }} !!!!</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const msg = ref('hello');
    const htmlStr = ref('<strong>hello</strong>');
    return { msg, htmlStr };
  },
};
</script>

<style scoped>

</style>