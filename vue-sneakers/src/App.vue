<script setup>
import {ref, watch, provide, computed} from "vue";


import Header from "@/components/Header.vue";
import Drawer from "@/components/Drawer.vue";

/*Cart (START)*/
const cart = ref([]);
const isCreatingOrder = ref(false);

const drawerOpen = ref(false)

const closeDrawer = () =>{
  drawerOpen.value = false;
}
const openDrawer = () =>{
  drawerOpen.value = true;
}

const totalPrice = computed(
    ()=> cart.value.reduce((acc, item)=> acc + item.price, 0)
);
const vatPrice = computed(
    ()=> Math.round(( totalPrice.value * 5) / 100)
);


const cartIsEmpty = computed(()=> cart.value.length === 0);

const cartButtonDisabled = computed(()=> isCreatingOrder.value || cartIsEmpty.value);


const addToCart = (item) => {
  cart.value.push(item);
  item.isAdded = true;
}

const createOrder = async ()=>{
  try{
    isCreatingOrder.value = true;
    const {data} = await axios.post('https://0f19d9182f91cfff.mokky.dev/orders', {
      items: cart.value,
      totalPrice: totalPrice.value,
    })
    cart.value = [];

    return data;
  }catch (err) {
    console.log(err)
  }
  finally {
    isCreatingOrder.value = false;
  }

}

const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false;
}

watch(cart, ()=>{
      localStorage.setItem('cart', JSON.stringify(cart.value))
    },
    {deep: true}
);

provide('cart', {
  cart,
  closeDrawer,
  openDrawer,
  addToCart,
  removeFromCart
});

/*Cart (END)*/


// watch(filters, fetchItems);

</script>

<template>
  <Drawer
      v-if="drawerOpen"
      :total-price="totalPrice"
      :vat-price="vatPrice"
      @create-order="createOrder"
      :button-disabled="cartButtonDisabled"
  />
  <div class="bg-white w-4/5	m-auto rounded-xl shadow-xl mt-14">
    <Header :total-price="totalPrice" @open-drawer="openDrawer"/>

    <div class="p-10">
      <router-view></router-view>
    </div>

  </div>
</template>

<style scoped>

</style>
