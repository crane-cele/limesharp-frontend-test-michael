<template>
    <div class="mx-auto">
      <div class="flex flex-col items-center">
        <h1 class="font-bold text-center">Experienced & Multi-Talented</h1>
        <img src="../assets/underline.svg" />
        <p class="text-[#65757E] text-center text-sm">
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam tortor leo, porttitor vel dictum at, aliquam et augue. Duis vel molestie risus, ut lobortis felis.
        </p>

      </div>
    
      <div class="grid items-start">
        <GridItem 
          v-for="(item, index) in items" 
          :key="index" 
          :description="item.description"
          :isExpanded="index === expandedIndex"
          @toggle-expand="toggleExpand(index)"
        />
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  import GridItem from './GridItem.vue';
  
  export default defineComponent({
    name: 'Grid',
    components: {
      GridItem
    },
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
  
      const expandedIndex = ref<number | null>(null);
  
      const toggleExpand = (index: number) => {
        expandedIndex.value = expandedIndex.value === index ? null : index;
      };
  
      return {
        items,
        expandedIndex,
        toggleExpand
      };
    }
  });
  </script>
  