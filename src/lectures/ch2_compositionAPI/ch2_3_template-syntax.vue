<template>
  <div>
    <h2>보간법</h2>
    <p>{{ message }}</p>
    <p v-once>{{ message }}</p> <!--1회성으로 저장-->
    <button v-on:click="(message = message + '!')">Click</button>
    <hr />
    <h2>v-html</h2>
    <p>{{ rawHtml }}</p> <!--html을 text로 인식함-->
    <p v-html="rawHtml"></p> <!--html을 html로 인식함-->
    <hr />
    <h2>속성 바인딩</h2>
    <div v-bind:title="dynamicTitle">마우스를 올려보세요</div>
    <input type="text" value="홍길동" v-bind:disabled="isInputDisabled" />
    <input v-bind="attrs" /> <!--패스워크 객체 들어감-->
    <hr />
    <h2>JavaScript</h2>
    {{ message.split('').reverse().join('') }}<br />
    {{ isInputDisabled ? '예' : '아니요' }}
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const message = ref('안녕하세요');
    const rawHtml = ref('<strong>안녕하세요</strong>');

    const dynamicTitle = ref('안녕하세요!!!!');
    const isInputDisabled = ref(true);
    const attrs = ref({
      type: 'password',
      value: '12345678',
      disabled: false,
    })

    return {
      message,
      rawHtml,
      dynamicTitle,
      isInputDisabled,
      attrs,
    };
  },
};
</script>

<style lang="scss" scoped>

</style>