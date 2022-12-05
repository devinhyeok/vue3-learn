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
  </div>
</template>

<script setup>
import { ref } from 'vue';
import PostItem from './PostItem.vue';
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
</script>

<style scoped>

</style>