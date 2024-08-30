<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer')

    // 椭圆
    const ellipse = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(118, 30, 5000),
      ellipse: {
        semiMajorAxis: 20000, // 半长轴
        semiMinorAxis: 10000, // 半短轴
        height: 3000,
        extrudedHeight: 6000,
        rotation: Math.PI/4, // 指定椭圆从北逆时针旋转
        material: Cesium.Color.GREEN,
      }
    });

    // 矩形
    const rectangle = viewer.entities.add({
      rectangle: {
        coordinates: Cesium.Rectangle.fromDegrees(120, 40, 123, 45),
        extrudedHeight: 30000,
        material: '/src/assets/baiquan1.webp'
      }
    });

    viewer.zoomTo(rectangle);

  })
  
  </script>
  
  <template>
    <div>14~15 entity实体（椭圆、立体）</div>
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
  