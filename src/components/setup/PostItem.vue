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
// 일반 스크립트는 컴포넌트 불러올때 발생함
console.log('Normal Script');
</script>

<script setup>
import { computed } from '@vue/reactivity';

// Setup 함수는 Element가 생성할 때마다 발생함
console.log('Script Setup');

// setup 함수에서 prop 정의 하는법
const props = defineProps({
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
  },
  isLike: {
    type: Boolean,
    default: false,
  },
  obj: {
    type: Object,
    default: () => ({}),
  },
});

// setup 함수에서 이벤트 정의 하는법
const emit = defineEmits(['toggleLike'])

const isLikeClass = computed(() =>
  props.isLike ? 'btn-danger' : 'btn-outline-danger',
);
const typeName = computed(() =>
  props.type === 'news' ? 'news' : 'notice',
);
const toggleLike = () => {
  emit('toggleLike');
};
</script>

<style>

</style>