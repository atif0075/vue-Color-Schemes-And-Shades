<template>
  <section class="min-h-screen h-screen relative bg-yellow-50">
    <div
      class="absolute h-60 w-60 mix-blend-multiply filter blur-2xl bg-purple-300 rounded-full left-[30%] top-[10%] animate-blob"
    ></div>
    <div
      class="absolute animate-blob h-60 w-60 mix-blend-multiply filter blur-2xl opacity-50 bg-yellow-500 rounded-full left-[40%] top-[0]"
    ></div>
    <div
      class="absolute h-60 animate-blob w-60 mix-blend-multiply filter blur-2xl opacity-50 bg-pink-500 rounded-full left-[50%] top-[0]"
    ></div>
    <main class="h-full bg">
      <div id="nav" class="h-16 w-full flex justify-center items-center">
        <router-link
          class="py-1 px-4  shadow-md ml-3 border-2 relative z-10 border-yellow-100 text-yellow-900"
          to="/"
        >Home</router-link>
        <router-link
          class="py-1 px-4  shadow-md ml-3 border-2 relative z-10 border-yellow-100 text-yellow-900"
          to="/about"
        >About</router-link>
      </div>
      <router-view />
    </main>
  </section>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
