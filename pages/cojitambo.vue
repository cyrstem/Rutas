<template>
    <div>
        <dloader />
    </div>
</template>
<script>
import dloader from '@/components/dloader'

export default {
  components: { dloader },
    layout:'controls',
    name:'tester',

    data() {
      return {
      };
    },
    mounted() {
      
    },
    methods:{
     
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