<template>
  <div class="container">
    <div class="title-bar">
      <div class="title prevent-select draggable">Custom Title Bar</div>
      <div class="control prevent-select">
        <button id="min" @click="windowControll('minimize')">
          <i class="fa fa-window-minimize"></i>
        </button>
        <button id="max" @click="windowControll('maximize')">
          <i class="fa fa-window-maximize"></i>
        </button>
        <button id="close" @click="windowControll('close')">
          <i class="fa fa-window-close"></i>
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ipcRenderer} from "electron";

const windowControll = (type) => {
  ipcRenderer.send('windowController',type)
}
</script>

<style scoped>
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  margin: 0px;
}

body *{
  box-sizing: border-box;
}

.container{
  height: 100%;
  padding: 0;
  display: grid;
  grid-template-rows: auto 1fr;
}

.title{
  height: auto;
  padding: 10px;
  display: inline-block;
}

.control{
  float: right;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  margin-top: 5px;
  margin-right: 5px;
  width: 100px;
}

.control button{
  padding: 5px;
  background: #000000;
  color: #ffffff;
  outline: 0;
  border: 0;
}

.control button:hover{
  background: #444444
}

.title-bar{
  background: #000000;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  color: #ffffff;
  font-size: 15px;
}

.prevent-select{
  user-select: none;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
}

.draggable{
  -webkit-app-region: drag;
}
</style>
