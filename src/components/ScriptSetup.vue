<template>
  <div class="container py-4">
    {{ msg }}
    <br />
    {{ message }}
    <input v-model="message" type="text" />
    <button @click="sayHello">click</button>
    <PostItem
      type="news"
      title="title"
      contents="contents"
      :is-like="true">
    </PostItem>
    <hr />
    <TemplateRefsChild ref="child"></TemplateRefsChild>
    <template v-if="child">{{ child.message }}</template>
    <hr />
    <MyButton class="parent-class"></MyButton>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';
import PostItem from './PostItem.vue';
import MyButton from './setup/MyButton.vue';
import TemplateRefsChild from './setup/TemplateRefsChild.vue';

const msg = 'Hello World';
const message = ref('');
const sayHello = () => {
  alert('Hello World');
};
const child = ref(null);
defineExpose({
  msg,
});

// Api 자주 호출하면 오류남 시간차를 두고 사용할 것
// 원래 async 함수 안에서 await를 써야하지만 setup 함수는 이를 허용해줌
const response = await axios(
  'https://dummy.restapiexample.com/api/v1/employees',
);
console.log('response: ', response);
</script>

<style scoped>

</style>