<template>
    <div class="rounded-lg overflow-hidden shadow-lg">
      <div class="bg-[#57655f] h-24 flex">
        <img src="../assets/mark.svg" width="22" alt="mark" />
      </div>

      <div class="flex flex-col gap-3 p-4 bg-blac">
        <h2 class="text-xl font-bold text-center">BLOCK</h2>
        <p class="m-auto text-center" :class="{ 'line-clamp-2': !isExpanded }">{{ description }}</p>
        <button @click="$emit('toggle-expand')" class="flex items-center justify-center">
          <img v-if="!isExpanded" src="../assets/plus.png" />
          <img v-else src="../assets/minus.svg" />
        </button>
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    name: 'GridItem',
    props: {
      description: {
        type: String,
        required: true
      },
      isExpanded: {
        type: Boolean,
        required: true
      }
    }
  });
  </script>
  
  <style scoped>
  .line-clamp-2 {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;  
    overflow: hidden;
  }
  </style>
  