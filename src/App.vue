<script>
import { computed, ref, reactive, toRef, toRefs } from 'vue'

export default {
  setup() {
    const message = ref("Hello")

    const item = reactive({
      name: "Product 1",
      price: 10,
      quantity:1
    })

    const increment = () => item.quantity++
    const decrement = () => item.quantity--

    const swapProduct = () => {
      item.name = "Product A"
      item.price = 30
      item.quantity = 2
    }


    const total = computed(() => item.price * item.quantity)

    const { name, price, quantity } = toRefs(item);


    return {
      message,
      increment,
      decrement,
      swapProduct,
      name,
      price,
      quantity,
      total
    }
  }
}

</script>

<template>
  <h1>{{ name }} : {{ price }}</h1>
  <button class="button" @click="swapProduct">Swap product</button>
  <button class="button" @click="price++">Increment price</button>
  <h2>{{ quantity }}</h2>
  <button class="button" @click="increment">+</button>
  <button class="button" @click="decrement">-</button>

  <h3>Total: {{ total }}</h3>
</template>

<style scoped></style>
