<template>
  <div class="container">
    <div class="header">
      <h1 class="title">Experienced & Multi-Talented</h1>
      <img src="../assets/underline.svg" alt="underline" />
      <p class="description">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam tortor leo, porttitor vel dictum at, aliquam et augue. Duis vel molestie risus, ut lobortis felis.
      </p>
    </div>

    <div class="grid-container">
      <GridItem 
        v-for="(item, index) in items" 
        :key="index" 
        :description="item.description" 
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import GridItem from './GridItem.vue';

export default defineComponent({
  name: 'Grid',
  components: { GridItem },
  setup() {
    const items = ref([
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
      { description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut vestibulum eros nisi, eu sagittis nisl feugiat quis.' },
    ]);

    return {
      items,
    };
  }
});
</script>

<style scoped>
.container {
  @apply w-full px-4 py-8;
}
.header {
  @apply flex flex-col items-center gap-6;
}
.title {
  @apply text-4xl font-bold text-center font-gotham-bold;
}
.description {
  @apply text-[#65757E] mb-8 text-center max-w-[645px] text-sm font-proximaNova-regular;
}
.grid-container {
  @apply grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-9 items-start;
}
</style>
