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
 methods: {
    init() {
        const container = document.getElementById('container');
        this.mesh = new Three.Object3D();

        this.camera = new Three.PerspectiveCamera(45, window.innerWidth/window.innerHeight, 0.25, 20);
        this.camera.position.z = 1;

        this.scene = new Three.Scene();

        // let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2);
        // let material = new Three.MeshNormalMaterial();

        // this.mesh2 = new Three.Mesh(geometry, material);
        // this.scene.add(this.mesh2);
     

        const loader = new GLTFLoader().setPath('model/');
        loader.load('Cojitambo.gltf', (gltf)=>{
            this.mesh = gltf.scene
            this.scene.add(gltf.scene)
        })
       
        this.renderer = new Three.WebGLRenderer({antialias: true});
        this.renderer.setSize(window.innerWidth,window.innerHeight);
        this.renderer.setClearColor(0xF9F8ED,1)
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
   
  },
  mounted() {
      this.init();
      this.render();
      window.addEventListener( 'resize', this.onWindowResize );
  },
 
       
    

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
