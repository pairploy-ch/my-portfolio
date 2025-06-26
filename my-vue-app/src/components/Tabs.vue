<script setup>
import { onMounted, ref } from "vue";

const categories = ref([]);

onMounted(async () => {
  try {
    const res = await fetch("http://localhost:3001/api/categories");
    categories.value = await res.json();
  } catch (err) {
    console.error("❌ Error fetching portfolio:", err);
  }
});

// import { Camera, Menu } from "lucide-vue-next";
</script>
<script>
export default {
  data() {
    return {
      tab: 'All',
    };
  },
  methods: {
    setTab(name) {
      this.tab = name;
      this.$emit('tab', this.tab);
    },
  },
};
</script>
<template>
  <div>
    <ul
      class="flex flex-wrap text-sm font-medium text-center text-gray-500 dark:text-gray-400"
    >
      <li class="me-2">
        <a
         @click="setTab('All')"
          :class="tab === 'All' ? 'linear-bg' : ''"
          class="inline-block px-4 py-3 rounded-lg cursor-pointer"
          aria-current="page"
          >All</a
        >
      </li>
      <li class="me-2" v-for="item in categories">
        <a
          @click="setTab(item.name)"
          :class="tab === item.name ? 'linear-bg' : ''"
          class="cursor-pointer inline-block px-4 py-3 rounded-lg hover:text-gray-900 hover:bg-gray-100 dark:hover:bg-gray-800 dark:hover:text-white"
          >{{ item.name }}</a
        >
      </li>
    </ul>
  </div>
</template>
<style>
.linear-bg {
  background-image: linear-gradient(to right, #2d2fe1, #732eb5);
  color: #fff;
}
</style>
