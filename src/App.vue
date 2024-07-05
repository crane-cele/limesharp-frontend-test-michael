<template>
  <div class="min-h-screen bg-[#1c2026] text-white flex items-center justify-center p-4">
    <Grid />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Grid from './components/Grid.vue';

export default defineComponent({
  name: 'App',
  components: {
    Grid
  }
});
</script>