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
import { onMounted, ref } from "vue";

const items = ["html", "css"];
const works = ref([]);
const techs = ref([]);

onMounted(async () => {
  try {
    const res = await fetch("http://localhost:3001/api/works");
    works.value = await res.json();

    const response = await fetch("http://localhost:3001/api/tech");
    techs.value = await response.json();
  } catch (err) {
    console.error("❌ Error fetching portfolio:", err);
  }
});

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
      tab: "All",
    };
  },
  methods: {
    tabs(name) {
      this.tab = name;
    },
  },
};
</script>

<template>
  <div>
    <NavBar />

    <router-view />

    <Footer class="mt-20" />
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
