<script setup lang="ts">
interface Props {
  folderName: string;
  imagen: string; // "CARPETAAZUL.png"
}

const props = defineProps<Props>();
</script>

<template>
  <div
    class="flex flex-col justify-center items-center size-25 cursor-pointer hover:bg-white/30 hover:rounded-md hover:transition-all"
  >
    <img
      :src="`/img/icons/${props.imagen}`"
      class="icon-image"
      :alt="props.folderName"
    />
    <span>{{ props.folderName }}</span>
  </div>
</template>