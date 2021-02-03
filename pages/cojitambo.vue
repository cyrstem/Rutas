<template>
    <div>
        <div ref="container" id="container">
        </div>
    </div>
</template>
<script>

//import test from '@/test.js'

export default {
    layout:'controls',
    name:'tester',

    data() {
      return {
        // model:{},
        // objects:[],
        // activeMesh: {},
        // isLoaded: false,
        // autoRotate: true
      };
    },
    mounted() {
      // const { autoRotate } = this;
      // this.scene =SceneInit({ rootEl: this.$refs.container, autoRotate});
      // this.loadModel();
    },
    methods:{
      // loadModel(){
      //   this.isLoaded = false;
      //   this.scene.loadModel('model/scene1.gltf', (model)=>{
      //     model.name = 'tester';

      //   })
      //   this.model = model
      //   this.scene.add(model)

      //   setTimeout(() =>{
      //     this.isLoaded = true
      //   }, 200)
      // }
    }
}
</script>

<style>

#container{
  width: 100%;
  height: 100%;
  overflow: hidden;
  animation: 2s appear;
  z-index: 0;
}

@keyframes appear {
  0% {
    opacity: 0;
  }

}
canvas {
    width: 100% !important;
    height: 95vh !important;
 }
</style>