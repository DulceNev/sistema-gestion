<script setup lang="ts">
import { ref } from "vue";
import { Icon } from "@iconify/vue";

const username = ref("");
const router = useRouter();

function handleFakeLogin() {
  localStorage.setItem("nombreUsuario", username.value);
  router.push("/home");
  console.log({
    username: username.value,
  });
}
</script>

<template>
  <div class="background-image">
    <div class="h-screen w-screen">
      <div
        class="flex flex-col justify-center h-full items-center gap-3 text-primary"
      >
        <img src="../public/img/user-image.png" alt="" />
        <form
          @submit.prevent="handleFakeLogin"
          class="flex flex-col gap-3 items-center"
          action=""
        >
          <input
            v-model="username"
            class="bg-white/30 rounded-full py-1 px-4 w-56"
            type="text"
            placeholder="Nombre..."
            required
          />
          <input
            class="bg-white/30 rounded-full py-1 px-4 w-56 outline-none autofill:bg-white/30"
            type="password"
            placeholder="Contraseña... "
            autocomplete="new-password"
            required
          />
          <button
            type="submit"
            class="bg-pink-200 flex items-center justify-center gap-1 text-md w-full rounded-full p-1 cursor-pointer hover:scale-110 transition-all"
          >
            <p>Entrar</p>
            <Icon
              icon="pixelarticons:arrow-right"
              width="24"
              height="24"
              style="color: #48264b"
            />
          </button>
        </form>
      </div>
    </div>
  </div>
</template>