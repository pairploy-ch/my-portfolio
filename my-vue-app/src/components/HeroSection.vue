<script setup>
import ButtonMain from "./ButtonMain.vue";
import ButtonSecon from "./ButtonSecon.vue";
import { onMounted, ref } from 'vue';

const inf = ref([])

onMounted(async () => {
  try {
    const res = await fetch('http://localhost:3001/api/tech')
    inf.value = await res.json()
  } catch (err) {
    console.error('❌ Error fetching portfolio:', err)
  }
})
</script>

<template>
  <div style="background-color: #f7f4fb" class="w-full mt-16">
    <div class="w-full start-0 border-b border-gray-200">
      <div
        class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4 h-200 grid grid-cols-2"
      >
        <div class="">
          <p
            class="mb-6 text-lg font-normal text-black lg:text-xl mt-5"
          >
            Hello, I am
          </p>
          <h1
            style="
              line-height: 70px;
              background: linear-gradient(#2d2fe1, #732eb5);
              -webkit-background-clip: text;
              background-clip: text;
              -webkit-text-fill-color: transparent;
            "
            class="mb-4 text-4xl font-extrabold leading-none tracking-tight text-gray-900 md:text-5xl lg:text-6xl"
          >
           <!-- {{ inf[0].name }} -->
           UX/UI Designer & <br />
           Web Developer
          </h1>
          <p
            class="text-lg font-normal text-gray-500 lg:text-xl mt-5"
          >
            Being a dedicated employee with team player, fast learner and time
            management skills, experiencing in several front end coding & UX/UI
            Designing projects
          </p>
          <div class="flex mt-10 pb-32">
            <ButtonMain :text="'Go To Portfolio'" />
            <ButtonSecon class="ml-4" />
          </div>
        </div>
        <div class="">
          <img
            width="600"
            class="h-auto max-w-full"
            src="../assets/profile-img.png"
            alt="image description"
          />
        </div>
      </div>
    </div>
  </div>
</template>
