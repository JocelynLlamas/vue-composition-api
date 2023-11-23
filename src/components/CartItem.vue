<script>
import { reactive, toRefs, computed } from 'vue';

export default {
  props:{
    cartItem:{
      type: Object,
      required: true
    }
  },
  setup(props) {
    // console.log(props.cartItem)

    const item = reactive(props.cartItem)

    const increment = () => item.quantity++

    const decrement = () => item.quantity--
    
    const total = computed(()=> item.price * item.quantity)

    const { name, price, quantity } = toRefs(item)

    return {
      quantity,
      name,
      price,
      total,
      increment,
      decrement,
    }
  }
}
</script>

<template>
  <h1>{{ name }} : {{ price }} : {{ quantity }}</h1>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>

  <h3>Total: {{ total }}</h3>
</template>

<style scoped></style>
