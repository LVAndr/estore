<script setup>
import Card from "@/components/Card.vue";

defineProps({
  items: Array
})



</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
    v-for="item in items"
    :key="item.id"
        :title="item.title" :price="item.price" :image-url="item.imageUrl"
    :is-favorite="item.isFavorite"
    />
<!--    :is-added="true" :is-favorite="true" :on-click-add="onClick"-->
  </div>
</template>

<style scoped>

</style>