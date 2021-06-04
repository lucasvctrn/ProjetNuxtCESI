<template>
    <div v-if="item" class="bg-center overflow-hidden text-green-900 h-screen">
        <div class="flex">
            <div class="ml-10 rounded overflow-hidden w-3/12 flex-none">
                <img v-if="item.image" :src=" 'http://localhost:1337' + item.image.url" class="w-full">
            </div>
                <div>
                    <div>
                    <h1 class="mt-6 font-bold text-5xl">{{ item.name }}</h1>
                </div>
                <div>
                    <h2 class="mt-4 mb-4 font-semi-bold text-4xl">{{ item.price }} €</h2>
                </div>
                <div>
                    <p class="text-xl ml-4"> {{ item.description }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            item: null
        }
    },
    created() {
        const id = this.$route.params.id;
        this.$axios.$get(`products/${id}`).then((response) => {
            this.item = response;
        })
    }
}
</script>