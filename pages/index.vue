<template>
  <div class="container border rounded">
    <div>
      <h1 class="title">
        Rutas
      </h1>
      <div class="flex justify-between">
        <NuxtLink
        class="flex bg-white text-black items-center justify-center w-24 text-sm px-4 py-2 leading-none border rounded text-black border-black hover:border-transparent hover:text-teal-700 hover:bg-red mt-4 lg:mt-0"
        to="/cojitambo">
        Ruta 1</NuxtLink>

        <NuxtLink 
        class="flex bg-white text-black items-center justify-center w-24 text-sm px-4 py-2 leading-none border rounded text-black border-black hover:border-transparent hover:text-teal-700 hover:bg-red mt-4 lg:mt-0"
        to ="/avVolcanes">Ruta 2
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // layout: 'main'
}
</script>
<style >

.container {
  margin: 0 auto;
  height: 100vh;
  width:100%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  overflow: hidden;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color:black;
  letter-spacing: 1px;
}

</style>
