<script setup>
import * as Cesium from 'cesium'
import { onMounted } from 'vue'
import { userToken } from './optionConfig.js'

onMounted(()=>{
  Cesium.Ion.defaultAccessToken = userToken;
  // 所有api的开始
  
  const viewer = new Cesium.Viewer('cesiumContainer')

  // 经纬度 转笛卡尔
  // 返回的是一个笛卡尔坐标 ( z 轴不是高度)
  const cartesian1 = Cesium.Cartesian3.fromDegrees(110, 20, 20); // 经度 纬度 高度
  console.log('cartesian1=>', cartesian1)

  // 笛卡尔 转 弧度坐标
  const cartographic1 = Cesium.Cartographic.fromCartesian(cartesian1);
  console.log('cartographic1=>', cartographic1)
  // 弧度转角度坐标
  // const lon = 180 / Math.PI * cartographic1.longitude;
  // const lat = 180 / Math.PI * cartographic1.latitude;
  const lon = Cesium.Math.toDegrees(cartographic1.longitude);
  const lat = Cesium.Math.toDegrees(cartographic1.latitude);
  console.log(`lon=>${lon} lat=>${lat} height=>${cartographic1.height}`)
})

</script>

<template>
  <div>6 坐标转化</div>
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
