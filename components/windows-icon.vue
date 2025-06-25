<script setup lang="ts">
interface Props {
  folderName: string;
  imagen: string; // "CARPETAAZUL.png"
}

const props = defineProps<Props>();

const emit = defineEmits<{
  (e: "abrir"): void;
}>();
</script>

<template>
  <div
    @click="emit('abrir')"
    class="flex flex-col justify-center items-center h-25 w-25 cursor-pointer hover:bg-white/30 hover:rounded-md hover:transition-all"
  >
    <img
      :src="`/img/icons/${props.imagen}`"
      class="icon-image"
      :alt="props.folderName"
    />
    <span>{{ props.folderName }}</span>
  </div>
</template>