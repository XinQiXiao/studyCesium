<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  import { userToken } from './optionConfig.js'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = userToken;
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {
      infoBox: false, // 隐藏右侧信息框
      selectionIndicator: false, // 不显示选中的状态
    })

     // 标注
     const billboard = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(120, 30, 100),
      billboard: {
        image: '/src/assets/position_white.png',
        scale: 0.3,
        color: Cesium.Color.RED,
      }
    })

    // 线
    const polyline = viewer.entities.add({
      polyline: {
        positions: Cesium.Cartesian3.fromDegreesArrayHeights([120, 30, 0, 120, 30, 100]), // 返回笛卡尔坐标数组
        width: 2,
        material: Cesium.Color.RED,
      },
     
    })

    // label
    const label = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(120, 30, 100),
      label: {
        text: '地点A',
        fillColor: Cesium.Color.GREEN,
        // showBackground: true,
        // backgroundColor: new Cesium.Color(255, 0, 0)
        pixelOffset: new Cesium.Cartesian2(0, -50),
      }
    })

    viewer.zoomTo(billboard);

    // 组合实体
    const entitys = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(120.0005, 30.0005, 100),
      billboard: {
        image: '/src/assets/position_white.png',
        scale: 0.3,
        color: Cesium.Color.GREEN,
      },
      polyline: {
        positions: Cesium.Cartesian3.fromDegreesArrayHeights([120.0005, 30.0005, 0, 120.0005, 30.0005, 100]), // 返回笛卡尔坐标数组
        width: 2,
        material: Cesium.Color.GREEN,
      },
      label: {
        text: '地点B',
        fillColor: Cesium.Color.BLUE,
        // showBackground: true,
        // backgroundColor: new Cesium.Color(255, 0, 0)
        pixelOffset: new Cesium.Cartesian2(0, -50),
      }
    })
  })

  
  
  </script>
  
  <template>
    <div>16 entity实体（组合）</div>
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
  