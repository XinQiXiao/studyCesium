<script setup>
import * as Cesium from 'cesium'
import { onMounted } from 'vue'

onMounted(()=>{
  Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
  // 所有api的开始
  
  const viewer = new Cesium.Viewer('cesiumContainer', {
    timeline: false, // 时间轴
    animation: false, // 动画按钮
    geocoder: false, // 搜索按钮
    homeButton: false, // 主页按钮
    sceneModePicker: false, // 投影按钮
    baseLayerPicker: false, // 图层选择按钮
    navigationHelpButton: false, // 帮助按钮
    fullscreenButton: false, // 全屏控制按钮
  })
})

</script>

<template>
  <div>5 cesium控件</div>
  <div id="cesiumContainer">
    
  </div>
  
</template>

<style scoped>
#cesiumContainer {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

</style>
<style>
.cesium-viewer-bottom {
  display: none;
}
</style>
