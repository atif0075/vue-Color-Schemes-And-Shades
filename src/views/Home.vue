<template>
  <div class="flex flex-col w-full items-center justify-center relative z-10">
    <div class="w-80">
      <input
        type="text"
        class="my-3 border-2 outline-none py-2 px-2 border-yellow-200 text-yellow-900"
        v-model="getVal"
      />
      <button
        class="px-4 py-2 border-2 font-medium border-yellow-200 bg-yellow-200 text-yellow-800"
        @click="get"
      >Generate</button>
    </div>
    <div class="border-2 my-2 border-yellow-50 text-yellow-900 relative z-10">
      <select v-model="getVal2" class="w-80 py-2 outline-none">
        <option value="monochrome">Monochromatic</option>
        <option value="monochrome-dark">Monochrome Dark</option>
        <option value="monochrome-light">Monochrome Light</option>
        <option value="analogic">Analogic</option>
        <option value="analogic-complement">Analogic Complement</option>
        <option value="triad">Triad</option>
        <option value="complement">Complement</option>
        <option value="quad">Quad</option>
      </select>
    </div>
  </div>
  <div class="h-80 w-full flex justify-center my-7">
    <div v-if="load" class="flex flex-col justify-center w-80">
      <div id="bg0" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt0 }}</span>
      </div>
      <div id="bg1" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt1 }}</span>
      </div>
      <div id="bg2" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt2 }}</span>
      </div>
      <div id="bg3" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt3 }}</span>
      </div>
      <div id="bg4" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt4 }}</span>
      </div>
      <div id="bg5" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt5 }}</span>
      </div>
      <div id="bg6" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt6 }}</span>
      </div>
      <div id="bg7" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt7 }}</span>
      </div>
      <div id="bg8" class="h-full py-2 px-1">
        <span class="bg-gray-800 text-gray-50">{{ txt8 }}</span>
      </div>
    </div>
    <div v-else>loading</div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      load: false,
      getVal: "fcef8a",
      getVal2: "monochrome",
      txt0: "",
      txt1: "",
      txt2: "",
      txt3: "",
      txt4: "",
      txt5: "",
      txt6: "",
      txt7: "",
      txt8: "",


    }
  },
  created() {
    this.get()

  },
  methods: {
    async fetchColor() {
      const res = await fetch(`https://www.thecolorapi.com/scheme?hex=${this.getVal}&mode=${this.getVal2}&count=9`)
      const data = await res.json()
      return data
    },
    async get() {
      this.load = false
      const data = await this.fetchColor()
      this.load = true
      setTimeout(() => {
        bg0.style.background = data.colors[0].hex.value
        bg1.style.background = data.colors[1].hex.value
        bg2.style.background = data.colors[2].hex.value
        bg3.style.background = data.colors[3].hex.value
        bg4.style.background = data.colors[4].hex.value
        bg5.style.background = data.colors[5].hex.value
        bg6.style.background = data.colors[6].hex.value
        bg7.style.background = data.colors[7].hex.value
        bg8.style.background = data.colors[8].hex.value
      }, 200);
      setTimeout(() => {
        this.txt0 = data.colors[0].name.value + " " + data.colors[0].hex.value
        this.txt1 = data.colors[1].name.value + " " + data.colors[1].hex.value
        this.txt2 = data.colors[2].name.value + " " + data.colors[2].hex.value
        this.txt3 = data.colors[3].name.value + " " + data.colors[3].hex.value
        this.txt4 = data.colors[4].name.value + " " + data.colors[4].hex.value
        this.txt5 = data.colors[5].name.value + " " + data.colors[5].hex.value
        this.txt6 = data.colors[6].name.value + " " + data.colors[6].hex.value
        this.txt7 = data.colors[7].name.value + " " + data.colors[7].hex.value
        this.txt8 = data.colors[8].name.value + " " + data.colors[8].hex.value
      }, 700);
    }



  },
}
</script>
