<script setup>
import Card from './Card.vue'
import { inject } from 'vue'; 

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Add')
}

const addToFavorite = inject('addToFavorite')

</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :onClickAdd="onClickAdd"
      :onClickFavorite="() => addToFavorite(item)"
      :is-favorite="item.isFavorite"
    />
  </div>
</template>
