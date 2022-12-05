<template>
  <main>
    <div class="container text-center py-4">
      <PostCreate @create-post="createPost"></PostCreate>

      <hr class="my-4" />

      <div class="row g-3">
        <div v-for="post in posts" :key="post.id" class="col col-4">
          <PostItem
            :title="post.title"
            :contents="post.contents"
            :type="post.type"
            :isLike="post.isLike"
            @toggleLike="post.isLike = !post.isLike">
          </PostItem>
        </div>
      </div>

      <hr class="my-4" />

      <!--Non-Prop 속성: props로 선언되지 않는 속성 (class, style, id) 등등-->
      <!--Non-Prop 속성은 html root element에 상속됨-->
      <!--이미 자식 속성이 있는 경우-->
      <!--id, style: (class="parent-class") => (class="parent-class child-class")-->
      <LabelInput
        v-model="username"
        label="name"
        class="parent-class"
        style="color: red"
        id="parent-id">
      </LabelInput>
    </div>
  </main>
</template>

<script>
import { reactive, ref } from 'vue';
import PostItem from './PostItem.vue';
import PostCreate from './PostCreate.vue';
import LabelInput from './LabelInput.vue';
import LabelTitle from './LabelTitle.vue';
import Username from './Username.vue';

export default {
  setup() {
    const obj = reactive({
      title: 'title2',
      contents: 'contents2',
    });
    const posts = reactive([
      { id: 1, title: 'title1', contents: 'contents1', isLike: true, type: 'news' },
      { id: 2, title: 'title2', contents: 'contents2', isLike: true, type: 'news' },
      { id: 3, title: 'title3', contents: 'contents3', isLike: true, type: 'news' },
      { id: 4, title: 'title4', contents: 'contents4', isLike: false, type: 'notice' },
      { id: 5, title: 'title5', contents: 'contents5', isLike: true, type: 'news' },
    ]);
    const createPost = (newPost) => {
      console.log('newPost: ', newPost);
      posts.push(newPost);
    };

    const username = ref('');
    const firstname = ref('12');
    const lastname = ref('123');

    return { obj, posts, createPost, username, firstname, lastname };
  },
  components: {
    PostItem,
    PostCreate,
    LabelInput,
  }
}
</script>

<style>

</style>