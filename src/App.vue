<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
// import Drawer from './components/Drawer.vue'

const items = ref([])

onMounted(async () => {
  // fetch('http://localhost:8000').then(res => res.json()).then(data => {
  //   console.log(data);
  // })
  // axios.get('http://localhost:8000').then(resp=>console.log(resp.data));

  try {
    const { data } = await axios.get('http://localhost:8000')
    // console.log(data)
    items.value = data
  } catch (error) {
    console.log(error)
  }
})
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">All items</h2>

        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none" name="" id="">
            <option value="">By name</option>
            <option value="">By Price(low to high)</option>
            <option value="">By Price(high to low)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="Search" />
            <input
              class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="Search..."
            />
          </div>
        </div>
      </div>

      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>
