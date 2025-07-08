<script setup lang="ts">
import { Icon } from "@iconify/vue";

const now = useNow();
const formattedTime = computed(() => {
  return now.value
    .toLocaleTimeString("en-US", {
      hour: "2-digit",
      minute: "2-digit",
      hour12: true,
    })
    .toLowerCase();
});
const nombreUsuario = useLocalStorage("nombreUsuario", "");
</script>

<template>
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
      <p class="text-xl">{{ formattedTime }}</p>
    </div>
  </footer>
</template>