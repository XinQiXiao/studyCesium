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

    let lon = 120, lat = 30, num = 0;

    // CallbackProperty 生成一个动态的实体
    const polyline = viewer.entities.add({
      polyline: {
        positions: new Cesium.CallbackProperty(()=>{
          num+=0.0001
          console.log('num=>', num)
          lon+=num
          lat+=num
          if(lon<130){
            return Cesium.Cartesian3.fromDegreesArray([120, 30, lon, lat])
          } else {
            polyline.polyline.positions = Cesium.Cartesian3.fromDegreesArray([120, 30, 130, 40])
          }
          
        }, false), // 必须传false 不传动不起来
        width: 5,
        material: Cesium.Color.RED,
      },
     
    })
    // viewer.zoomTo(polyline);
    
  })
  
  </script>
  
  <template>
    <div>18 callBack property</div>
    
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
  