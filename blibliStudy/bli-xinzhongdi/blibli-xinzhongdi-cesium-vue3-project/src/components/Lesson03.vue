<script setup>
import * as Cesium from 'cesium'
import { onMounted } from 'vue'
import { userToken } from './optionConfig.js'

onMounted(()=>{
  Cesium.Ion.defaultAccessToken = userToken;
  // 所有api的开始
  // 默认影像图层
  // const viewer = new Cesium.Viewer('cesiumContainer')
  // 加载 ArcGis影像图层
  const esri = new Cesium.ArcGisMapServerImageryProvider({
    url: 'https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer',
    enablePickFeatures: false,
  })
  const viewer = new Cesium.Viewer('cesiumContainer', {
    imageryProvider: esri, // 自定义 默认是google的影像图层
    terrainProvider: Cesium.createWorldTerrain({
      requestWaterMask: true,
    }), // 地形图层
  })
})

</script>

<template>
  <div>2 第一个Cesium页面</div>
  <div>3 Vue+vite+cesium</div>
  <div>4 hello cesium</div>
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
