<script setup lang="ts">
import Modal from "~/components/modal.vue";
import WindowsIcon from "~/components/windows-icon.vue";
</script>

<template>
  <div class="background-image p-5">
    <Modal class="absolute" />
    <div
      class="grid grid-cols-4 md:grid-cols-6 lg:grid-cols-10 h-screen items-start"
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
  </div>
</template>