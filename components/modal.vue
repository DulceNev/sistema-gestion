<script setup lang="ts">
import { Icon } from "@iconify/vue";
import { useDraggable } from "@vueuse/core";
import { useTemplateRef } from "vue";

interface Props {
  title: string;
  text?: string;
  color: string;
}

interface Task {
  text: string;
  isCompleted: boolean;
}

const props = defineProps<Props>();

const el = useTemplateRef<HTMLElement>("el");

const { x, y, style } = useDraggable(el, {
  initialValue: { x: 81, y: 228 },
});

const textInputValue = ref("");
// Voy a tener un array de objetos tipo Task
const todoList = ref<Task[]>([]);

function addTask() {
  todoList.value.push({
    text: textInputValue.value,
    isCompleted: false,
  });
  textInputValue.value = "";
}

function deleteTask(index: number) {
  todoList.value.splice(index, 1);
}
</script>

<template>
  <div :style="style" style="position: fixed" class="w-[500px] text-primary">
    <header
      ref="el"
      class="flex justify-between items-center px-2 rounded-t-md"
      :style="{ backgroundColor: props.color }"
    >
      <p class="text-xl text-white!">{{ props.title }} {{ x }} {{ y }}</p>
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
    <div class="flex bg-white/80 rounded-b-md flex-col items-center p-2 gap-3">
      <li
        class="flex gap-2 items-center justify-between w-full"
        v-for="(task, index) in todoList"
        :key="index"
      >
        <div class="flex gap-2">
          <input
            type="checkbox"
            class="checkbox checkbox-sm checkbox-primary"
            v-model="task.isCompleted"
          />

          <!-- Si task.isCompleted es true, aplica la clase line-through. -->
          <p :class="{ 'line-through': task.isCompleted }">
            {{ task.text }}
          </p>
        </div>

        <button @click="deleteTask(index)">
          <Icon
            icon="pixelarticons:close"
            width="28"
            style="color: #93c3ff"
            class="cursor-pointer"
          />
        </button>
      </li>
      <form
        @submit.prevent="addTask"
        class="flex justify-center items-center gap-3 w-full"
      >
        <input
          v-model="textInputValue"
          placeholder="Agregar tarea..."
          required
          class="py-1 w-full border-1 text-primary text-center rounded-md cursor-pointer"
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