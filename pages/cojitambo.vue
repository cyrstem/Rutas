<template>
    <div>
        <div ref="container" id="container">
        </div>
    </div>
</template>
<script>

import * as THREE from "three";
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader'
import {OBJLoader} from 'three/examples/jsm/loaders/OBJLoader'
import {OrbitControls} from 'three/examples/jsm/controls/OrbitControls'
export default {
    layout:'controls',
    name:'tester',

    data(){
        return{
            camera: null,
            scene: null,
            renderer:null,
            gltf:null,
            orbit_control:null,
        };
    },
    methods:{
      init(){
          let container = this.$refs.container;
          this.camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,100)
          this.camera.position.set(0,2,5)
          this.scene = new THREE.Scene()
          this.renderer = new THREE.WebGLRenderer({ antialias: true });
          this.renderer.setClearColor("#000000");
          this.renderer.setSize(window.innerWidth, window.innerHeight);
          container.appendChild(this.renderer.domElement);
      ///Geometry
          const geometry = new THREE.BoxGeometry();
          const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
          const cube = new THREE.Mesh( geometry, material );
          this.scene.add( cube );


       // SET ORBIT CONTROLS
          this.orbit_controls = new OrbitControls(
            this.camera,
            this.renderer.domElement
          )
          this.orbit_controls.addEventListener("change", () =>
            this.renderer.render(this.scene, this.camera)
          )
      },
      loadModel() {
        const loader = new GLTFLoader();
        loader.load(
          // resource URL
          'model/cojitambo.gltf',
          // called when the resource is loaded
          function ( gltf ) {

            this.scene.add( gltf.scene );

            gltf.animations; // Array<THREE.AnimationClip>
            gltf.scene; // THREE.Group
            gltf.scenes; // Array<THREE.Group>
            gltf.cameras; // Array<THREE.Camera>
            gltf.asset; // Object

          },
          // called while loading is progressing
          function ( xhr ) {

            console.log( ( xhr.loaded / xhr.total * 100 ) + '% loaded' );

          },
          // called when loading has errors
          function ( error ) {

            console.log( 'An error happened'+ error );
            

          }
        );
    },
      onResize(){
        window.addEventListener('resize',() =>
        this.renderer.setSize(window.innerWidth,window.innerHeight),
        this.camera.aspect = window.innerWidth/window.innerHeight,
        this.camera.updateProjectionMatrix()
        )
      },
      doshow(){
           this.renderer.render(this.scene,this.camera)
          this.renderer.setPixelRatio(window.devicePixelRatio)
      },
    
    },
mounted() {

this.init();
this.onResize();
this.doshow();
this.loadModel();

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