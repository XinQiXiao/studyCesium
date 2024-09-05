<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  import { userToken } from './optionConfig.js'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = userToken;
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})
  
    // 实体 entity
    // 写法一
    // const point = new Cesium.Entity({
    //   position: Cesium.Cartesian3.fromDegrees(120, 30),
    //   point: {
    //     pixelSize: 20, // 点像素大小
    //     color: Cesium.Color.BLUE,
    //   },
    // });
    // viewer.entities.add(point)
    // viewer.zoomTo(point);

    // 写法二(推荐)
    const point2 = viewer.entities.add({
      id: 'point',
      position: Cesium.Cartesian3.fromDegrees(121, 30),
      point: {
        pixelSize: 20, // 点像素大小
        color: Cesium.Color.BLUE,
      }
    })
    viewer.zoomTo(point2);

  })
  
  </script>
  
  <template>
    <div>9 点线面</div>
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
  