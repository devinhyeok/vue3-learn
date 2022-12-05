<template>
  <div class="p-3 bg-danger">
    <button class="btn btn-primary" type="button" @click="sayHello">
      My Button
    </button>
  </div>
</template>

<script>
export default {
  // inheritAttrs: false, // 속성 상속 봉인!
  emit: ['click'],
  setup(props, { emit }) {
    // 자동 상속을 막아도 이렇게 setup시 들어오긴해서 수동으로 설정 가능
    // console.log('context.attrs: ', context.attrs);
    // console.log('class: ', context.attrs.class);
    // console.log('id: ', context.attrs.id);
    // console.log('onClick: ', context.attrs.onClick);
    const sayHello = () => {
      emit('sayHello');
    };
    return { sayHello };
  }
}
</script>

<style scoped>

</style>