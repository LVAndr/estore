<script setup>
import Card from "@/components/Card.vue";

defineProps({
  items: Array,

})

const emit = defineEmits(['addToFavorite'])



</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
    v-for="item in items"
    :key="item.id"
    :id="item.id"
    :title="item.title"
    :image-url="item.imageUrl"
    :price="item.price"
    :on-click-favorite="()=> emit ('addToFavorite', item)"
    :is-favorite="item.isFavorite"
    />
<!--    :is-added="true" :is-favorite="true" :on-click-add="onClickAdd"-->
  </div>
</template>

<style scoped>

</style>