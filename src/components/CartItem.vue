<script setup>
import {
  reactive,
  toRefs,
  computed,
  onMounted,
  onUnmounted,
  onUpdated,
} from "vue";

const props = defineProps({
  cartItem: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["remove"]);

const item = reactive(props.cartItem);

const increment = () => item.quantity++;

const decrement = () => item.quantity--;

const total = computed(() => item.price * item.quantity);

const { name, price, quantity } = toRefs(item);

const remove = () => emit("remove", item);

// Lifecycle Hooks
onMounted(() => {
  // console.log('Component mounted.')
});

onUnmounted(() => {
  // console.log('Component Unmounted.')
});

onUpdated(() => {
  // console.log('Component updated.')
});
</script>

<template>
  <h1>{{ name }} : {{ price }} : {{ quantity }}</h1>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <br />
  <button @click="remove">Remove</button>

  <h3>Total: {{ total }}</h3>
</template>

<style scoped></style>
