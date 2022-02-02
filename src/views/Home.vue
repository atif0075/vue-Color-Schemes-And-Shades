<template>
  <div class="home flex justify-between flex-wrap h-56 w-full">
    <div id="bg1" class="bg-green-400 w-32 h-20"></div>
    <div id="bg2" class="bg-green-400 w-32 h-20"></div>
    <div id="bg3" class="bg-green-400 w-32 h-20"></div>
    <div id="bg4" class="bg-green-400 w-32 h-20"></div>
    <div id="bg5" class="bg-green-400 w-32 h-20"></div>
    <div id="bg6" class="bg-green-400 w-32 h-20"></div>
    <div id="bg7" class="bg-green-400 w-32 h-20"></div>
    <div id="bg8" class="bg-green-400 w-32 h-20"></div>
    <div id="bg9" class="bg-green-400 w-32 h-20"></div>
  </div>
  <div>
    <button class="px-3 py-2 bg-green-200 text-green-800" @click="api">Generate</button>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {

    }
  },
  methods: {
    async api() {
      console.clear()
      fetch("https://www.thecolorapi.com/scheme?hex=0047AB&count=10", {
        method: "GET"
      }).then(function (response) {
        return response.json();
      }).then(function (data) {
        console.log(data.mode);
        bg1.style.background = data.colors[0].hex.value
        bg1.style.background = data.colors[1].hex.value
        bg2.style.background = data.colors[2].hex.value
        bg3.style.background = data.colors[3].hex.value
        bg4.style.background = data.colors[4].hex.value
        bg5.style.background = data.colors[5].hex.value
        bg6.style.background = data.colors[6].hex.value
        bg7.style.background = data.colors[7].hex.value
        bg8.style.background = data.colors[8].hex.value
        bg9.style.background = data.colors[9].hex.value
      })
      console.log("done")
    }
  },
}
</script>
