<template>
  <div  class="flex flex-row my-2 text-center justify-center  ">
    <router-link to="/" class="focus:bg-green-300 hover:bg-green-400 hover:text-white px-10 py-2 rounded-md mr-5 transition-all ease-in-out duration-300 ">Home</router-link> 
    <router-link :to="{name : 'Quiz'} " class="hover:bg-green-400 hover:text-white  px-10 py-2 rounded-md transition-all ease-in-out duration-300">Quiz</router-link> 
  </div>

  <router-view/>
</template>

<style>

</style>
