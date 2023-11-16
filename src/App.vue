<script>
import {reactive, ref, toRef, toRefs} from 'vue';

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
    
    // const nameRef = toRef(item, 'name');
    // console.log('nameRef:', nameRef.value)
    // item.name = "New Product"
    // console.log('nameRef:', nameRef.value)

    const {name, price} = toRefs(item)

    // console.log('name:', itemRefs.name.value)
    // console.log('price:', itemRefs.price.value)
    
    // item.name = "Hot Product"
    // item.price = 50

    // console.log('name:', itemRefs.name.value)
    // console.log('price:', itemRefs.price.value)

    return{
      message,
      quantity,
      name,
      price,
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
  <h2>{{ quantity }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
</template>

<style scoped>
</style>
