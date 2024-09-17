<script setup>
import Card from './Card.vue'

const onClickAdd = () => {
  alert('Add')
}
</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      title="Nike Blazer Mid Suede shoes"
      imageUrl="/sneakers/sneakers-1.jpg"
      :price="120"
      :isAdded="false"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
