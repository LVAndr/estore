<script setup>
import {inject} from "vue";
import CartItem from "@/components/CartItem.vue";

const {cart, removeFromCart} = inject('cart');


</script>

<template>
<div class="flex flex-1 flex-col gap-4" v-auto-animate>
  <CartItem
      v-for="item in cart"
      :key="item.id" :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
      @on-click-remove="()=> removeFromCart(item)"
  />


</div>
</template>

<style scoped>

</style>