<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  import { userToken } from './optionConfig.js'

  let viewer;
  let pointA, pointB;
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = userToken;
    // 所有api的开始
    
    viewer = new Cesium.Viewer('cesiumContainer', {
      infoBox: false, // 隐藏右侧信息框
      selectionIndicator: false, // 不显示选中的状态
    })

     //
     pointA = viewer.entities.add({
      id: 'pointA',
      position: Cesium.Cartesian3.fromDegrees(121, 30),
      point: {
        pixelSize: 20, // 点像素大小
        color: Cesium.Color.BLUE,
      }
    })

    pointB = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(121.0001, 30.0001),
      point: {
        pixelSize: 20, // 点像素大小
        color: Cesium.Color.RED,
      }
    })

    viewer.zoomTo(pointA)


    console.log(viewer.entities)
    
  })

  function delEntityClick(){
    // 直接删除
    // viewer.entities.remove(pointA)

    // 删除全部
    // viewer.entities.removeAll();

    // 通过ID删除
    // viewer.entities.removeById('pointA')

    // 先拿后删
    const entity = viewer.entities.getById('pointA')
    viewer.entities.remove(entity)
  }
  
  </script>
  
  <template>
    <div>17 entity实体(删除)</div>
    <el-button @click="delEntityClick">删除</el-button>
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
  