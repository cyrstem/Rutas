<template>
  <div class="container z-0">
    <div>
      <h1 class="title">
        Rutas
      </h1>
      <div class="flex justify-between">
        <NuxtLink
        class="flex bg-white text-black items-center justify-center w-24"
        to="/cojitambo">
        Ruta 1</NuxtLink>

        <NuxtLink 
        class="flex bg-white text-black items-center justify-center w-24"
        to ="/avVolcanes">Ruta 2
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>
<style>
body{
    background-color: #768596;
  }

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #35495e;
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
  color:white;
  letter-spacing: 1px;
}
</style>
