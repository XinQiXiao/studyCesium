<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})
  
    const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);

    // setView 通过定义相机目的地（方向），直接跳转到目的地
    viewer.camera.setView({
      destination: position,
      orientation: { // 默认（0, -90, 0）
        heading: Cesium.Math.toRadians(0), // y轴旋转方向
        pitch: Cesium.Math.toRadians(0), // x轴旋转方向
        roll: Cesium.Math.toRadians(0), // z轴旋转方向
      },
    })
  })
  
  </script>
  
  <template>
    <div>7 相机</div>
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
  