<template>
  <div class="row">
    <div class="col col-2">
      <select v-model="type" class="form-select" aria-label="Default select example">
        <option value="news">news</option>
        <option value="notice">notice</option>
      </select>
    </div>
    <div class="col col-8">
      <input v-model="title" type="text" class="form-control" />
    </div>
    <div class="col col-2 d-grid">
      <button class="btn btn-primary" @click="createPost">button</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  emits: {
    createPost: ({ type, title }) => {
      if (!type || !title) {
        return false;
      }
      return true;
    }
  },
  setup(props, { emit }) {
    const type = ref('news');
    const title = ref('');
    const createPost = () => {
      const newPost = {
        type: type.value,
        title: title.value,
      };
      emit('createPost', newPost);
      type.value = 'news';
      title.value = '';
    };
    return { createPost, title, type };
  }
};
</script>

<style scoped>

</style>