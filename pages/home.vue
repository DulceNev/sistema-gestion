<script setup lang="ts">
// import { Heart, Icon, Volume2, Wifi } from "lucide-vue-next";
import { Icon } from "@iconify/vue";
import Modal from "~/components/modal.vue";
import WindowsIcon from "~/components/windows-icon.vue";

const nombreUsuario = ref("");

onMounted(() => {
  const nombreGuardado = localStorage.getItem("nombreUsuario");
  // ¿Hay algo en nombreGuardado?
  if (nombreGuardado) {
    nombreUsuario.value = nombreGuardado;
  }
});
</script>

<template>
  <div class="background-image">
    <!-- <Modal class="absolute" color="#93c3ff" title="NOTAS" /> -->
    <div
      class="h-screen grid grid-cols-4 md:grid-cols-6 lg:grid-cols-10 items-start p-5"
    >
      <div class="flex flex-col gap-6">
        <WindowsIcon folderName="CARPETA" imagen="CARPETAAZUL.png" />
        <WindowsIcon folderName="TODO LIST" imagen="TODO.png" />
        <WindowsIcon folderName="CARPETA" imagen="CARPETAROSA.png" />
        <WindowsIcon folderName="NOTAS" imagen="NOTES.png" />
      </div>
      <div class="flex flex-col gap-6">
        <WindowsIcon folderName="POMODORO" imagen="POMODORO.png" />
        <WindowsIcon folderName="CARPETA" imagen="CARPETAMORADA.png" />
        <WindowsIcon folderName="CALENDARIO" imagen="CALENDARIO.png" />
      </div>
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
            <NuxtLink to="/inicio-sesion">
              <a class="flex gap-2">
                <Icon icon="pixelarticons:user" width="24" height="24" />Cerrar
                sesión</a
              ></NuxtLink
            >
          </li>

          <li>
            <a
              ><Icon icon="pixelarticons:moon" width="24" height="24" />
              Suspender</a
            >
          </li>
          <li>
            <a
              ><Icon
                icon="pixelarticons:power"
                width="24"
                height="24"
              />Apagar</a
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
  </div>
</template>