<script setup>
  import * as Cesium from 'cesium'
  import { onMounted } from 'vue'
  
  onMounted(()=>{
    Cesium.Ion.defaultAccessToken = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI4NTYzNjEwZC1kODRkLTQ3YWMtOWM0Ny1mYTAxYTQ0NDI1MTIiLCJpZCI6MjM0Mjc0LCJpYXQiOjE3MjM0NzIzNTB9.erRR0UJ-3jMrzQSa6udAIyxjLb142DdsN42fihQYAu4';
    // 所有api的开始
    
    const viewer = new Cesium.Viewer('cesiumContainer', {})

    // 标注
    const billboard = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(116, 40, 10),
      billboard: {
        image: '/src/assets/position_white.png',
        scale: 0.3,
        color: Cesium.Color.YELLOW,
      }
    })

    const label = viewer.entities.add({
      position: Cesium.Cartesian3.fromDegrees(116, 30, 10),
      label: {
        text: 'Cesium',
        fillColor: Cesium.Color.GREEN,
        showBackground: true,
        backgroundColor: new Cesium.Color(255, 0, 0)
      }
    })

    viewer.zoomTo(label);
  })
  
  </script>
  
  <template>
    <div>10 标注</div>
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
  