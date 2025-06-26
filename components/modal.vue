<script setup lang="ts">
import { Maximize, Minus, X } from "lucide-vue-next";
</script>

<template>
  <div class="w-[500px] bg-white/90 border-7 rounded-xl">
    <header
      class="flex justify-between border-b-7 items-center p-2 rounded-t-md bg-[#93c3ff]"
    >
      <p class="text-xl text-white!">NOTAS</p>
      <div class="flex gap-3">
        <Minus class="cursor-pointer" color="#fff" />
        <Maximize class="cursor-pointer" color="#fff" />
        <X class="cursor-pointer" color="#fff" />
      </div>
    </header>
    <header class="flex flex-col justify-between items-center p-2">
      <textarea
        class="w-full h-full text-lg font-light"
        name=""
        id=""
      ></textarea>
      <button
        class="border-3 rounded-lg py-1 px-4 shadow-custom my-2 bg-white cursor-pointer"
      >
        Crear nota
      </button>
    </header>
  </div>
</template>