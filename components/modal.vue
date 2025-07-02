<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { Minus } from "lucide-vue-next";

interface Props {
  title: string;
  text?: string;
  color: string;
}

const props = defineProps<Props>();
</script>

<template>
  <div
    class="w-[500px] bg-white/90 border-7 border-primary rounded-xl text-primary"
  >
    <header
      class="flex justify-between border-b-7 border-primary items-center px-2 rounded-t-md"
      :style="{ backgroundColor: props.color }"
    >
      <p class="text-xl text-white!">{{ props.title }}</p>
      <div class="flex gap-3">
        <Minus class="cursor-pointer" color="#fff" />
        <Icon
          icon="pixelarticons:scale"
          width="24"
          height="24"
          style="color: #fff"
        />
        <Icon
          icon="pixelarticons:close"
          width="24"
          height="24"
          style="color: #fff"
        />
      </div>
    </header>
    <div class="flex flex-col justify-between items-center p-2">
      <!-- <textarea

        placeholder="Se supone que debes escribir algo aquí..."
        class="w-full h-full text-lg font-light"
        name=""
        id=""
      ></textarea>
      <button
        class="border-3 rounded-lg py-1 px-4 my-2 bg-white cursor-pointer border-[#48264B] color-[#48264B]"
      >
        Crear nota
      </button> -->
      <div class="flex gap-3 items-center">
        <input
          type="checkbox"
          defaultChecked
          className="checkbox checkbox-primary checkbox-sm"
        />
        <p class="">Esto es una tarea</p>
      </div>
    </div>
  </div>
</template>