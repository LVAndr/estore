<script setup>

import Card from "./Card.vue";


const onClick = ()=>{
  alert(222)
}
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card title="Мужские Кроссовки Nike Blazer Mid Suede" :price="2300" image-url="/sneakers/sneakers-1.jpg"
    :is-added="true" :is-favorite="true"
    :on-click-add="onClick"
    />
    <Card/>
    <Card/>
    <Card/>
    <Card/>
  </div>
</template>

<style scoped>

</style>