<template>
    <div>
        <ul class="list-group my-5">
            <li class="list-group-item" v-for="item in items" :key="item.id">
                {{ item.title }} - {{ item.price }}
                <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">Remove from cart</button>
            </li>
        </ul>


        <div class="card p-3 my-5">
            <h4 class="text-center">${{ total }}</h4>
        </div>

        <button :disabled="cartEmpty" @click="$emit('pay')" class="btn btn-info form-control">Pay now</button>
    </div>
</template>

<script>
export default {
    props: ["items"],
    computed: {
        total() {
            return this.items.reduce((accumalator, item) => accumalator + Number(item.price), 0)
        },
        cartEmpty() {
            return items.length === 0
        }
    }
}
</script>
