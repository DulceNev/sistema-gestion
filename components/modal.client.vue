<script setup lang="ts">
import { Icon } from "@iconify/vue";

interface Props {
  title: string;
  classTextColor?: string;
  color: string;
}

const props = withDefaults(defineProps<Props>(), {
  classTextColor: "text-xl text-white!",
});
const modalX = useLocalStorage(`modal-x-${props.title}`, 81);
const modalY = useLocalStorage(`modal-y-${props.title}`, 228);
const draggable = useTemplateRef<HTMLElement>("draggable");

const { style, x, y } = useDraggable(draggable, {
  onEnd({ x, y }) {
    modalX.value = x;
    modalY.value = y;
  },
});
onMounted(() => {
  x.value = modalX.value;
  y.value = modalY.value;
});
</script>

<template>
  <div :style="style" style="position: fixed" class="w-[500px] text-primary">
    <header
      class="flex justify-between items-center px-2 rounded-t-md"
      :style="{ backgroundColor: props.color }"
    >
      <div ref="draggable" class="flex-1 cursor-grab">
        <p :class="classTextColor">{{ props.title }}</p>
      </div>
      <div class="flex gap-3">
        <Icon
          icon="ic:baseline-minus"
          width="24"
          height="24"
          style="color: #fff"
          class="cursor-pointer"
        />
        <Icon
          icon="pixelarticons:scale"
          width="24"
          height="24"
          style="color: #fff"
          class="cursor-pointer"
        />
        <Icon
          icon="pixelarticons:close"
          width="24"
          height="24"
          style="color: #fff"
          class="cursor-pointer"
        />
      </div>
    </header>
    <slot></slot>
  </div>
</template>