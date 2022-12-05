<template>
  <main>
    <div class="container py-4">
      <MyButton class="my-button" id="my-button" @say-hello="sayHello"></MyButton>
      <LabelInput label="name" data-id="i am id"></LabelInput>
      <hr />
      <FancyButton>Click!! <span style="color: red">@@@</span></FancyButton>
      <FancyButton>
        <template v-slot="{ fancyMessage }">{{ fancyMessage }}</template>
      </FancyButton>
      <hr />
      <AppCard>
        <!-- <template #[slotArgs]>title</template> -->
        <!-- <template #default>body</template> -->
        <!-- Body -->
        <!-- <template #footer>footer</template> -->
        <template #header="{ headerMessage }">
          {{ headerMessage }}
        </template>
        <template #default="{ childMessage, helloMessage }">
          default {{ message }}
          <br />
          {{ childMessage }}
          <br />
          {{ helloMessage }}
        </template>
        <template #footer="{ footerMessage }">
          {{ footerMessage }}
        </template>
      </AppCard>
      <hr />
      <AppCard>contents</AppCard>
    </div>
  </main>
</template>

<script>
import MyButton from './MyButton.vue';
import LabelInput from './LabelInput.vue';
import FancyButton from './FancyButton.vue';
import AppCard from './AppCard.vue';
import { ref } from 'vue';

export default {
  components: {
    MyButton,
    LabelInput,
    FancyButton,
    AppCard,
  },
  setup() {
    const sayHello = () => {
      alert('hello!');
    };
    const slotArgs = ref('header');
    const message = ref("hello from child");
    return { sayHello, slotArgs, message };
  }
}
</script>

<style scoped>

</style>