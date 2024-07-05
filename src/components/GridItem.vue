<template>
  <div class="grid-item">
    <div class="grid-item-header">
      <img src="../assets/mark.svg" width="22" alt="mark" />
    </div>

    <div class="grid-item-body">
      <h2 class="item-title">BLOCK</h2>
      <p :class="['item-description', { expanded: isExpanded }]" :style="{ height: paragraphHeight }" ref="descriptionParagraph">
        {{ description }}
      </p>
      <button @click="toggleExpand" class="expand-button">
        <img v-if="!isExpanded" src="../assets/plus.svg" width="10" alt="expand" class="max-w-max" />
        <img v-else src="../assets/minus.svg" width="10" alt="collapse" class="max-w-max" />
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, watch } from 'vue';

export default defineComponent({
  name: 'GridItem',
  props: {
    description: {
      type: String,
      required: true
    }
  },
  setup() {
    const descriptionParagraph = ref<HTMLElement | null>(null);
    const isExpanded = ref(false);
    const paragraphHeight = ref('62px');

    const updateHeight = () => {
      if (descriptionParagraph.value) {
        paragraphHeight.value = isExpanded.value
          ? descriptionParagraph.value.scrollHeight + 'px'
          : '62px';
      }
    };

    watch(isExpanded, updateHeight);

    const toggleExpand = () => {
      isExpanded.value = !isExpanded.value;
    };

    return {
      descriptionParagraph,
      isExpanded,
      paragraphHeight,
      toggleExpand,
    };
  }
});
</script>

<style scoped>
.grid-item {
  @apply bg-gray-800 rounded-t-lg overflow-hidden;
}
.grid-item-header {
  @apply bg-[#57655f] h-24 flex items-center justify-center;
}
.grid-item-body {
  @apply flex flex-col gap-3 p-4 bg-black;
}
.item-title {
  @apply text-[15px] font-bold text-center font-gotham-bold;
}
.item-description {
  @apply m-auto text-center text-[19px] text-[#65757E] max-w-[80%] font-proximaNova-regular overflow-hidden transition-all duration-1000;
}
.item-description.expanded {
  height: auto;
}
.expand-button {
  @apply flex items-center justify-center m-auto bg-[#1c2026] p-4 rounded-full w-[34px] h-[34px];
}
</style>
