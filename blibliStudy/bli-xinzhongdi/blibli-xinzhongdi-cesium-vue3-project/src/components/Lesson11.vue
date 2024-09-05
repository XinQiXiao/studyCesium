<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  import { userToken } from './optionConfig.js'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = userToken;
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})

    // 线
    const polyline = viewer.entities.add({
      polyline: {
        positions: Cesium.Cartesian3.fromDegreesArray([120, 40, 121, 41, 122, 40.5]), // 返回笛卡尔坐标数组
        width: 10,
        material: Cesium.Color.YELLOW,
      },
     
    })
    // viewer.zoomTo(polyline);

    // 多边形
    const redPolygon = viewer.entities.add({
      polygon: {
        hierarchy: Cesium.Cartesian3.fromDegreesArray([
          120.0,
          40.0,
          122.0,
          41.0,
          124.0,
          40.0
        ]),
        material: Cesium.Color.RED,
        height: 10000, // 高度
        extrudedHeight: 20000,
        outline: true, // 是否显示外线
        outlineColor: Cesium.Color.BLUE,
        fill: false,
      },
     
    })
    viewer.zoomTo(redPolygon);
  })
  
  </script>
  
  <template>
    <div>11-12 entity实体（线和多边型）</div>
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
  