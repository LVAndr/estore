<script setup>
import Card from "@/components/Card.vue";

</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card title="Мужские Кроссовки Nike Blazer Mid Suede" :price="2300" image-url="/sneakers/sneakers-1.jpg"
    :is-added="true" :is-favorite="true"
    :on-click-add="onClick"
    />
  </div>
</template>

<style scoped>

</style>