<template>
  <main>
    <div class="container text-center py-4">
      <div class="row g-3">
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
        <div class="col col-4">
          <AppCard></AppCard>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import AppCard from './AppCard.vue';

export default {
  setup() {
    return {};
  },
  components: { AppCard }
}
</script>

<style>

</style>