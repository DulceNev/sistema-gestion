<script setup lang="ts">
import { Icon } from "@iconify/vue";
import Modal from "~/components/Modal.vue";
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
const nombreUsuario = ref("");

onMounted(() => {
  const nombreGuardado = localStorage.getItem("nombreUsuario");
  // ¿Hay algo en nombreGuardado?
  if (nombreGuardado) {
    nombreUsuario.value = nombreGuardado;
  }
});

const windowsIconsChunks = computed(() => {
  const chunks = [];
  for (let i = 0; i < windowsIcons.length; i += MAX_ITEMS_PER_ROW) {
    chunks.push(windowsIcons.slice(i, i + MAX_ITEMS_PER_ROW));
  }

  return chunks;
});
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
    <footer
      class="fixed bottom-0 w-full bg-[#FFA7C8] px-5 py-2 flex justify-between items-center text-white"
    >
      <div class="dropdown dropdown-top cursor-pointer">
        <Icon
          tabindex="0"
          role="button"
          class="hover:scale-120 transition-all"
          icon="majesticons:heart"
          width="34"
          style="color: #fff"
        />
        <ul
          tabindex="0"
          class="dropdown-content font-medium menu bg-base-100 text-primary rounded-box z-1 w-60 p-2 shadow-sm"
        >
          <li>
            <NuxtLink to="/" class="flex gap-2">
              <Icon icon="pixelarticons:user" width="24" height="24" />Cerrar
              sesión</NuxtLink
            >
          </li>

          <li>
            <NuxtLink
              ><Icon icon="pixelarticons:moon" width="24" height="24" />
              Suspender</NuxtLink
            >
          </li>
          <li>
            <NuxtLink
              ><Icon
                icon="pixelarticons:power"
                width="24"
                height="24"
              />Apagar</NuxtLink
            >
          </li>
        </ul>
      </div>

      <div class="flex gap-3 items-center">
        <div class="tooltip" :data-tip="`Hola ${nombreUsuario}! :D`">
          <Icon
            icon="pixelarticons:mood-happy"
            width="24"
            height="24"
            style="color: #fff"
          />
        </div>

        <Icon
          icon="pixelarticons:cellular-signal-3"
          width="24"
          height="24"
          style="color: #fff"
        />
        <Icon
          icon="pixelarticons:volume-3"
          width="24"
          height="24"
          style="color: #fff"
        />
        <p class="text-xl">4:46 pm</p>
      </div>
    </footer>
    <Modal color="#93c3ff" title="TODO LIST" />
  </div>
</template>