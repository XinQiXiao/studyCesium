<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
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
    <div>13 entity实体（盒子、椭圆、立体）</div>
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
  