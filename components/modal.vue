<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { useDraggable } from "@vueuse/core";
import { useTemplateRef } from "vue";

interface Props {
  title: string;
  text?: string;
  color: string;
}

const props = defineProps<Props>();

const el = useTemplateRef<HTMLElement>("el");

const { x, y, style } = useDraggable(el, {
  initialValue: { x: 81, y: 228 },
});
</script>

<template>
  <div
    ref="el"
    :style="style"
    style="position: fixed"
    class="w-[500px] text-primary"
  >
    <header
      class="flex justify-between items-center px-2 rounded-t-md"
      :style="{ backgroundColor: props.color }"
    >
      <p class="text-xl text-white!">{{ props.title }}</p>
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
    <div
      class="flex bg-white/80 rounded-b-md flex-col justify-between items-center p-2 gap-3"
    >
      <div class="flex gap-3 items-center">
        <input type="checkbox" class="checkbox checkbox-sm checkbox-primary" />
        <p class="">Esto es una tarea</p>
      </div>
      <form action="" class="flex justify-center items-center gap-3 w-full">
        <input
          placeholder="Agregar tarea..."
          class="py-1 w-full border-1 text-primary text-center rounded-md cursor-pointer"
          required
        />
        <button
          :style="{ backgroundColor: props.color }"
          class="p-2 rounded-full cursor-pointer hover:brightness-95 active:brightness-90 active:scale-90 transition-all"
        >
          <Icon icon="material-symbols:add" width="24" style="color: #fff" />
        </button>
      </form>
    </div>
  </div>
</template>