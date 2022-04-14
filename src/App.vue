<template>
  <img
    src="./assets/bg_1.jpg"
    alt=""
    class="absolute top-0 object-fill h-screen w-screen filter blur-sm"
  />
  <div
    class="sticky top-0 z-50 flex flex-row mb-2 py-2 text-center justify-center font-bold text-white bg-opacity-40 backdrop-filter backdrop-blur-md shadow-lg rounded-br-2xl rounded-bl-2xl"
  >
    <router-link
      to="/"
      class="focus:bg-gray-300/10 z-10 bg-gray-400/50 hover:bg-slate-200/70 hover:text-black px-10 py-3 rounded-md mr-5 transition-all ease-in-out duration-300 hover:scale-105 backdrop-filter hover:backdrop-blur-2xl shadow-md"
      >Home</router-link
    >
    <router-link
      :to="{ name: 'Quiz' }"
      class="z-10 bg-gray-400/50 hover:bg-slate-200/70 hover:scale-105 hover:text-black px-10 py-2 rounded-md transition-all ease-in-out duration-300"
      >Quiz</router-link
    >
  </div>

  <router-view />
</template>

<style></style>
