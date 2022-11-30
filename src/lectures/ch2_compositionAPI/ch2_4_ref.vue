<template>
    <div>
        <p>{{ message }}</p> <!--ref는 message.value이 생략됨-->
        <button v-on:click="addMessage">add click</button>
    </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
    setup() {
        // ref는 변수가 하나밖에 없는 reactive와 같음
        let message = ref('Hello Vue!');
        // let message = reactive({ value: 'Hello Vue!' }); 
        const addMessage = () => {
            message.value = message.value + '!';
        };
        return {
            message,
            addMessage,
        };
    },
};
</script>

<style lang="scss" scoped>

</style>