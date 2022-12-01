<template>
  <div>
    <!--class-ref 바인딩-->
    <div :class="{ active: isActive, 'text-danger': hasError }">text</div>
    <!--class-object 바인딩-->
    <div :class="classObject">text</div>
    <!---->
    <div :class="[activeClass, errorClass]"></div>
    <button v-on:click="toggle">toggle</button>
    <button v-on:click="(hasError = !hasError)">toggleError</button>
  </div>
</template>

<script>
import { ref, computed } from 'vue';

export default {
  setup() {
    const isActive = ref(true);
    const hasError = ref(false);
    const classObject = computed(() => {
      return {
        active: isActive.value,
        'text-danger': hasError.value,
      }
    })
    const activeClass = ref('active')
    const errorClass = ref('text-danger')

    const toggle = () => {
      isActive.value = !isActive.value;
    }
    return {
      isActive,
      toggle,
      hasError,
      classObject,
      activeClass,
      errorClass
    };
  },
};
</script>

<style scoped>
.active {
  font-weight: 900;
}

.text-danger {
  color: red;
}
</style>