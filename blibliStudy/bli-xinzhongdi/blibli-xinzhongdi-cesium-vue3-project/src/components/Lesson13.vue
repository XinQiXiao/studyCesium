<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  import { userToken } from './optionConfig.js'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = userToken;
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})

    // 盒子
    const box = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(119, 30, 3000),
      box: {
        dimensions: new Cesium.Cartesian3(2000, 1000, 3000), // 长宽高
        material: Cesium.Color.RED,
      }
    });

    viewer.zoomTo(box);

  })
  
  </script>
  
  <template>
    <div>13 entity实体（盒子）</div>
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
  