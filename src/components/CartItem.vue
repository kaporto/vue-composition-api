<script>
import { computed, reactive, toRefs } from 'vue'

export default {
    props: {

        cartItem: {
            type: Object,
            required: true
        }
    },
    emits: 'remove',
    setup(props, {emit}) {

        const item = reactive(props.cartItem)

        const increment = () => item.quantity++
        const decrement = () => item.quantity--   

        const total = computed(() => item.price * item.quantity)

        const { name, price, quantity } = toRefs(item);

        const remove = () => emit('remove',item)

        return {
            increment,
            decrement,
            name,
            price,
            quantity,
            total,
            remove
        }
    }
}

</script>

<template>
    <h1>{{ name }} : {{ price }} : {{ quantity }}</h1>

    <button class="button" @click="increment">+</button>
    <button class="button" @click="decrement">-</button>
    <br>
    <button class="button" @click="remove">Remove</button>

    <h3>Total: {{ total }}</h3>
</template>

<style scoped></style>
