<script setup>

import DrawerHead from "@/components/DrawerHead.vue";
import CartItemList from "@/components/CartItemList.vue";
import InfoBlock from "@/components/infoBlock.vue";

const emit = defineEmits(['createOrder'])

const props = defineProps({
  totalPrice: Number,
  vatPrice: Number,
  buttonDisabled: Boolean
})

</script>

<template>
<div class="fixed top-0 left-0 h-full w-full z-10 bg-black opacity-70"></div>
  <div class="fixed right-0 top-0 z-20 bg-white w-96 h-full p-8">
    <DrawerHead/>

    <div
        v-if="!totalPrice"
         class="flex h-full items-center"
    >
      <InfoBlock

          title="Корзина пустая"
          description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ."
          image-url="/package-icon.png"
      />
    </div>

    <div v-else>
      <CartItemList/>


      <div class="flex flex-col gap-4 mt-7">
        <div class="flex gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{totalPrice}} руб.</b>
        </div>

        <div class="flex gap-2">
          <span>Налог 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{vatPrice}} руб.</b>
        </div>

        <button
            :disabled="buttonDisabled"
            @click="() => emit('createOrder')"
            class=" mt-4 bg-lime-500 w-full rounded-xl py-3 text-white cursor-pointer disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 transition"
        >
          Оформить заказ
        </button>
      </div>
    </div>


  </div>
</template>

<style scoped>

</style>