<template>
  <div>
    <div class="card">
      <div class="card-body">
        <span class="badge bg-secondary">{{ typename }}</span>
        <h5 class="card-title mt-2">{{ title }}</h5>
        <p class="card-text">{{ contents }}</p>
        <a href="#" class="btn" :class="isLikeClass" @click="toggleLike">likes</a>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from '@vue/reactivity';

export default {
  props: {
    type: {
      type: String,
      default: 'news',
      validator: value => {
        return ['news', 'notice'].includes(value);
      },
    },
    title: {
      type: String,
      required: true,
    },
    contents: {
      type: String,
      //required: true,
    },
    isLike: {
      type: Boolean,
      default: false,
    },
    obj: {
      type: Object,
      default: () => { },
    }
  },
  emit: ['toggleLike'],
  setup(props, context) {
    // console.log('props.title: ', props.title);
    const isLikeClass = computed(() =>
      props.isLike ? 'btn-danger' : 'btn-outline-danger'
    );
    const typename = computed(() =>
      props.type === 'news' ? 'news' : 'notice',
    );
    const toggleLike = () => {
      context.emit('toggleLike');
    }
    return { isLikeClass, typename, toggleLike };
  },
}
</script>

<style>

</style>