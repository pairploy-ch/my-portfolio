<script setup>
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";
import HeroSection from "./components/HeroSection.vue";
import CardService from "./components/CardService.vue";
import Tabs from "./components/Tabs.vue";
import Loading from "./components/Loading.vue";
import CardWork from "./components/CardWork.vue";
import Contact from "./components/Contact.vue";
import { Code, Wrench } from "lucide-vue-next";
import { onMounted, ref } from 'vue'

const items = ["html", "css"];
const works = ref([]);
const techs = ref([]);

onMounted(async () => {
  try {
    const res = await fetch('http://localhost:3001/api/works')
    works.value = await res.json();

    const response = await fetch('http://localhost:3001/api/tech')
    techs.value = await response.json();
   
  } catch (err) {
    console.error('❌ Error fetching portfolio:', err)
  }
})

// const portfolios = ref([])

// onMounted(async () => {
//   try {
//     const res = await fetch('http://localhost:3001/api/information')
//     portfolios.value = await res.json()
//   } catch (err) {
//     console.error('❌ Error fetching portfolio:', err)
//   }
// })

</script>
<script>
export default {
  data() {
    return {
      tab: 'All',
    };
  },
  methods: {
    tabs(name) {
      this.tab = name;
    }
  }
}
</script>

<template>
  <div>
   
   
  
    <HeroSection />
    <router-link to="/detail/1">About</router-link>
    <div style="margin-top: -130px" class="w-full start-0 border-gray-100">
      <div
        class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto grid grid-cols-3"
      >
        <CardService />
        <CardService />
        <CardService />
      </div>
    </div>
    <div class="w-full start-0 border-gray-100 mt-30">
      <div
        class="max-w-screen-xl flex flex-wrap flex-col items-center justify-between mx-auto"
      >
      
        <h3 class="text-4xl font-extrabold flex items-center mx-auto">
          <div class="div-icon mr-3">
            <Code />
          </div>
          Programs & Technologies
        </h3>
        <div class="mt-10 flex flex-wrap justify-center" :key="index">
          <img
            style="height: 80px; width: auto;"
            v-for="(item, index) in techs"
           
            class="h-auto max-w-full m-10"
            :src="item.img"
            :alt="item"
          />
        </div>
      </div>
    </div>

    <div class="w-full start-0 border-gray-100 mt-20">
      <div
        class="max-w-screen-xl flex flex-wrap flex-col items-center justify-between mx-auto"
      >
        <h3
          style="line-height: 50px"
          class="text-4xl flex items-center mx-auto text-center flex-col"
        >
          Let's Have a Look at

          <p
            class="font-extrabold"
            style="
              line-height: 70px;
              background: linear-gradient(#2d2fe1, #732eb5);
              -webkit-background-clip: text;
              background-clip: text;
              -webkit-text-fill-color: transparent;
            "
          >
            Portfolio
          </p>
        </h3>

        <div class="mt-10"> 
          <Tabs @tab="tabs" />
        </div>
        <div class="mt-10 w-full" v-for="(item, index) in works" >
          <CardWork v-if="item.type.name === tab || tab === 'All'" :item="item" />
          <!-- <router-link to="/detail">About</router-link> -->
        </div>
        <!-- <div class="mt-10 flex flex-wrap" :key="index">
          <img
            v-for="(item, index) in items"
            width="100"
            class="h-auto max-w-full m-10"
            :src="`/images/${item}.png`"
            :alt="item"
          />
        </div> -->
      </div>
    </div>
    <Contact />
   
  </div>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
</template>

<style scoped>
.div-icon {
  padding: 10px;
  background-image: linear-gradient(to right, #2d2fe1, #732eb5);
  border-radius: 10px;
  color: #fff;
}
</style>
