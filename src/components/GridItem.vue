<template>
  <div class="bg-gray-800 rounded-t-lg overflow-hidden">
    <div class="bg-[#57655f] h-24 flex items-center justify-center">
      <img src="../assets/mark.svg" width="22" alt="mark" />
    </div>

    <div class="flex flex-col gap-3 p-4 bg-black">
      <h2 class="text-[15px] font-bold text-center font-gotham-bold">BLOCK</h2>
      <p :class="[
        'm-auto',
        'text-center',
        'text-[19px]',
        'text-[#65757E]',
        'max-w-[80%]',
        'font-proximaNova-regular',
        'overflow-hidden',
        'transition-all',
        'duration-1000',
      ]"
      :style="{ height: paragraphHeight }"
      ref="descriptionParagraph"
      >
        {{ description }}
      </p>
      <button @click="toggleExpand"
        class="flex items-center justify-center m-auto bg-[#1c2026] p-4 rounded-full w-[34px] h-[34px]"
      >
        <img v-if="!isExpanded" src="../assets/plus.svg" width="10" class="max-w-max" />
        <img v-else src="../assets/minus.svg" width="10" class="max-w-max" />
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, nextTick } from 'vue';

export default defineComponent({
  name: 'GridItem',
  props: {
    description: {
      type: String,
      required: true
    },
  },
  setup() {
    const descriptionParagraph = ref<HTMLElement | null>(null);
    const isExpanded = ref(false);
    const paragraphHeight = ref('62px');

    const toggleExpand = () => {
      if (descriptionParagraph.value) {
        if (isExpanded.value) {
          paragraphHeight.value = '62px';
          nextTick(() => {
            isExpanded.value = false;
          });
        } else {
          nextTick(() => {
            const scrollHeight = descriptionParagraph.value!.scrollHeight + 'px';
            paragraphHeight.value = scrollHeight;
            nextTick(() => {
              isExpanded.value = true;
            });
          });
        }
      }
    };

    return {
      descriptionParagraph,
      paragraphHeight,
      isExpanded,
      toggleExpand,
    };
  },
});
</script>

<style scoped>
p {
  transition: height .7s ease;
}
</style>
