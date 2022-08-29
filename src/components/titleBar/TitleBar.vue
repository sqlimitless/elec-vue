<template>
  <v-layout style="height: 50px">
    <v-system-bar window class="draggable">
      <v-icon icon="mdi-message" class="mr-2"></v-icon>
      <span>상태바</span>
      <v-spacer></v-spacer>
      <v-btn icon="mdi-minus" variant="text" @click="windowControll('minimize')"></v-btn>
      <v-btn icon="mdi-checkbox-blank-outline" variant="text" class="ml-2" @click="windowControll('maximize')"></v-btn>
      <v-btn icon="mdi-close" variant="text" class="ml-2" @click="windowControll('close')"></v-btn>
    </v-system-bar>
  </v-layout>
</template>

<script setup lang="ts">
import {ipcRenderer} from "electron";

const windowControll = (type) => {
  ipcRenderer.send('windowController', type)
}
</script>

<style scoped>
.draggable{
  -webkit-app-region: drag;
}
</style>
