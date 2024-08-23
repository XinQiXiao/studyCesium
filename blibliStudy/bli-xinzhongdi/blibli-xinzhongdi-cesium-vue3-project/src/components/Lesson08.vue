<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})
  
    const position = Cesium.Cartesian3.fromDegrees(110, 20, 20000);

    // flyTo 快速切换飞行视角，带飞行动画，可以设置飞行时长
    // viewer.camera.flyTo({
    //   destination: position,
    //   orientation: { // 默认（0, -90, 0）
    //     heading: Cesium.Math.toRadians(0), // y轴旋转方向
    //     pitch: Cesium.Math.toRadians(0), // x轴旋转方向
    //     roll: Cesium.Math.toRadians(0), // z轴旋转方向
    //   },
    //   duratioin: 10, // 单位秒
    // })

    // lookAt 将视角固定在设置的点位上，可以选择视角，但不能改变位置
    const position2 = Cesium.Cartesian3.fromDegrees(110, 20);
    viewer.camera.lookAt(
      position2,
      new Cesium.HeadingPitchRange(
        Cesium.Math.toRadians(0),
        Cesium.Math.toRadians(-90),
        20000,
      )
    )
  })
  
  </script>
  
  <template>
    <div>8 飞行动画</div>
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
  