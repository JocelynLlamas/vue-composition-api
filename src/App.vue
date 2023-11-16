<script>
import { reactive, ref, toRef, toRefs, computed, watch, watchEffect } from 'vue';

export default {
  setup() {

    const message = ref('Hello')
    // If you are working with simple values, use ref function
    // const quantity = ref(1)
    // For more complex data structures or objects with multiple
    // propierties, use reactive function
    const item = reactive({
      name: "Product 1",
      price: 10,
      quantity: 1,
    })

    const increment = () => item.quantity++
    const decrement = () => item.quantity--
    const swapProduct = () => {
      item.name = "Product A"
      item.price = 30
    }


    const total = computed(()=> item.price * item.quantity)

    // const nameRef = toRef(item, 'name');
    // console.log('nameRef:', nameRef.value)
    // item.name = "New Product"
    // console.log('nameRef:', nameRef.value)

    const { name, price, quantity } = toRefs(item)

    // Is used to watch the changes in reactive data propierties or computed
    watch(()=>item.quantity, ()=>{
      if (item.quantity === 5) {
        alert('you cannt add more item')
      }
    }, {inmediate: true})

    watchEffect(()=>{
      console.log('Price changed:', item.price)
    })

    // console.log('name:', itemRefs.name.value)
    // console.log('price:', itemRefs.price.value)

    // item.name = "Hot Product"
    // item.price = 50

    // console.log('name:', itemRefs.name.value)
    // console.log('price:', itemRefs.price.value)

    return {
      message,
      quantity,
      name,
      price,
      total,
      increment,
      decrement,
      swapProduct
    }
  }
}
</script>

<template>
  <h1>{{ name }} : {{ price }}</h1>
  <button @click="swapProduct">Swap Product</button>
  <button @click="price++">Increment Price</button>
  <h2>{{ quantity }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>

  <h3>Total: {{ total }}</h3>
</template>

<style scoped></style>
