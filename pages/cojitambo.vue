<template>
    <div id="container">
    </div>
</template>
<script>
import * as Three from 'three'
import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';


export default {
    //layout:'Nav',
    name:'tester',
    data(){
        return {
        camera: null,
        scene: null,
        renderer: null,
        mesh: null
    }
},
 mounted() {
     this.$nextTick(() => {
      this.$nuxt.$loading.start()

      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
      this.init();
      this.render();
      //window.addEventListener( 'resize', this.onWindowResize );
  },
 methods: {
    init() {
        const container = document.getElementById('container');
        //this.mesh = new Three.Object3D();

        this.camera = new Three.PerspectiveCamera(45, window.innerWidth/window.innerHeight, 0.25, 20);
        this.camera.position.z =15 ;

        this.scene = new Three.Scene();


        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth,window.innerHeight);
        this.renderer.setClearColor(0xF9F8ED,1)
        this.light = new Three.DirectionalLight(0xffffff,1.8);
        this.light.position.x =60;
        this.light.position.y =100;
        this.light.position.z =20
        this.scene.add(this.light)
        const loader = new GLTFLoader().setPath('model/');
        loader.load('Cojitambo.gltf', (gltf)=>{
            this.mesh = gltf.scene
            this.scene.add(gltf.scene)
        })
       
       
        const controls = new OrbitControls(this.camera,this.renderer.domElement)
        //controls.minDistance = 20
        //controls.maxDistance= 100
        controls.target.set(0,0,0);
        controls.update();
        controls.addEventListener( 'change', this.render );
        container.appendChild(this.renderer.domElement);

    },
    onWindowResize(){
        camera.aspect = window.innerWidth / window.innerHeight;
		camera.updateProjectionMatrix();
        renderer.setSize( window.innerWidth, window.innerHeight );
        this.animate();
    },
    render() {
        requestAnimationFrame(this.render);
        // this.mesh.rotation.x += 0.01;
        // this.mesh.rotation.y += 0.02;
        
        this.renderer.render(this.scene, this.camera);
        
    }
   
  }
}
</script>
<style scoped>
#container{
   
    width: 100%;
    height: 100%;
}
    canvas{
        display: block;
        width: 100%;
        height: 100%;
    }
