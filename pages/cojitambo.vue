<template>
    <div>
        <div ref="container" id="container">
        </div>
    </div>
</template>
<script>

import * as THREE from "three";
import {GLTFLoader} from 'three/examples/jsm/loaders/GLTFLoader'
import {OrbitControls} from 'three/examples/jsm/controls/OrbitControls'


export default {
    layout:'controls',
    name:'tester',

    data(){
        return{
            camera: null,
            scene: null,
            renderer:null,
            // gltf:null,
             orbit_control:null,
            // transform_controls:null,
            
            assets:[],
            gltf_clicked_name:''
        };
    },
mounted() {

        let container = this.$refs.container;
        this.camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,1000)
        this.camera.position.set(0,2,5)
        this.scene = new THREE.Scene()

   
        // RENDER IN PAGE
    this.renderer = new THREE.WebGLRenderer({ antialias: true });
    this.renderer.setClearColor("#dbdbdb");
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

    window.addEventListener('resize',() =>
        this.renderer.setSize(window.innerWidth,window.innerHeight),
        this.camera.aspect = window.innerWidth/window.innerHeight,
        this.camera.updateProjectionMatrix()
    )

     // event resize---------------------------------------------
    //window.addEventListener('resize',() =>(
   // this.renderer.setSize(window.innerWidth, window.innerHeight);
    //this.camera.aspect = window.innerWidth/window.innerHeight; 
   // this.camera.updateProjectionMatrix();
    //)

    this.renderer.render(this.scene,this.camera)
    this.renderer.setPixelRatio(window.devicePixelRatio);

    // onResize(){
    //     // this.width = this.root.clientWidth
    // }
},

}
</script>

<style>

#container{
    animation: 1s appear;
}

@keyframes appear {
  0% {
    opacity: 0;
  }

  canvas {
    width: 100% !important;
    height: 100%;
 }
}
</style>