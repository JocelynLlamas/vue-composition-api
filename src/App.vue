<script>
import {reactive, ref} from 'vue';

export default{
  setup(){

    const message = ref('Hello')
    // If you are working with simple values, use ref function
    const quantity = ref(1)
    // For more complex data structures or objects with multiple
    // propierties, use reactive function
    const item = reactive({
      name: "Product 1",
      price: 10
    })

    const increment = () => quantity.value++
    const decrement = () =>quantity.value--
    const swapProduct = () => {
      item.name = "Product A"
      item.price = 30
    }

    return{
      message,
      quantity,
      item,
      increment,
      decrement,
      swapProduct
    }
  }
}
</script>

<template>
  <h1>{{ item.name }} : {{ item.price }}</h1>
  <button @click="swapProduct">Swap Product</button>
  <h2>{{ quantity }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
</template>

<style scoped>
</style>
