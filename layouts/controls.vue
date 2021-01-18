<template>
        <nav class="flex flex-wrap items-center justify-between p-2 bg-transparent">
             <NuxtLink 
                class="text-sm px-4 py-2 leading-none border rounded text-black border-black hover:border-black hover:text-white hover:bg-black mt-4 lg:mt-0"
                to ="/">Salir
            </NuxtLink>
            <Nuxt/> 
        </nav>
</template>
<style>
nav{
    z-index: 20000;
}
</style>