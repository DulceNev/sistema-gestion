<script setup lang="ts">
import { Icon } from "@iconify/vue";

// import { Heart, Icon, Volume2, Wifi } from "lucide-vue-next";

const windowsIcons = [
  { folderName: "CARPETA", imagen: "CARPETAAZUL.png" },
  { folderName: "TODO LIST", imagen: "TODO.png" },
  { folderName: "CARPETA", imagen: "CARPETAROSA.png" },
  { folderName: "NOTAS", imagen: "NOTES.png" },
  { folderName: "POMODORO", imagen: "POMODORO.png" },
  { folderName: "CARPETA", imagen: "CARPETAMORADA.png" },
  { folderName: "CALENDARIO", imagen: "CALENDARIO.png" },
];
const MAX_ITEMS_PER_ROW = 4;
const SIZE_WINDOWS_ICON = "125px";

const windowsIconsChunks = computed(() => {
  const chunks = [];
  for (let i = 0; i < windowsIcons.length; i += MAX_ITEMS_PER_ROW) {
    chunks.push(windowsIcons.slice(i, i + MAX_ITEMS_PER_ROW));
  }

  return chunks;
});
const textInputValue = ref("");
// Voy a tener un array de objetos tipo Task
const todoList = useLocalStorage<Task[]>("todos", []);

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
  <div class="background-image">
    <div class="h-screen p-5 relative flex gap-8">
      <div
        class="`grid gap-y-8 max-h-[100%] justify-start items-start`"
        v-for="(chunk, index) in windowsIconsChunks"
        :class="`grid-cols-[${SIZE_WINDOWS_ICON}]`"
        :key="index"
      >
        <template v-for="(icon, idx) in chunk" :key="idx">
          <WindowsIcon :folderName="icon.folderName" :imagen="icon.imagen" />
        </template>
      </div>

      <div class="flex flex-col gap-6"></div>
    </div>
    <Footer />
    <Modal color="red" title="TODO LIST 2">
      <div
        class="flex bg-white/80 rounded-b-md flex-col items-center p-2 gap-3"
      >
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
            :style="{ backgroundColor: '#93c3ff' }"
            class="p-2 rounded-full cursor-pointer hover:brightness-95 active:brightness-90 active:scale-90 transition-all"
          >
            <Icon icon="material-symbols:add" width="24" style="color: #fff" />
          </button>
        </form></div
    ></Modal>
    <Modal color="yellow" title="TODO LIST`3">
      <div
        class="flex bg-white/80 rounded-b-md flex-col items-center p-2 gap-3"
      >
        Lorem ipsum dolor sit amet consectetur, adipisicing elit. Eveniet
        aliquam ipsa consequuntur hic quaerat nobis dolore autem quisquam?
        Expedita soluta quia laborum odit et, tenetur ad sed? Sequi, repellat
        voluptates.
      </div></Modal
    >
    <Modal color="#93c3ff" title="TODO LIST">
      <div
        class="flex bg-white/80 rounded-b-md flex-col items-center p-2 gap-3"
      >
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
            :style="{ backgroundColor: '#93c3ff' }"
            class="p-2 rounded-full cursor-pointer hover:brightness-95 active:brightness-90 active:scale-90 transition-all"
          >
            <Icon icon="material-symbols:add" width="24" style="color: #fff" />
          </button>
        </form></div
    ></Modal>
  </div>
</template>