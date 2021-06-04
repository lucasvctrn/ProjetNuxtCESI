<template>
    <div>
        <div class="flex container justify-center">
            <nuxt-link :to="`ajoutproduit`" class="p-2 rounded bg-green-900 transition-all duration-150 ease-linear hover:bg-green-800 text-xl text-white">Ajouter un produit</nuxt-link>
        </div>
        <div v-for="product in items">
            <div class="flex items-center mb-2 container justify-center">
                <nuxt-link :to="`produit/${product.id}`" class="rounded bg-gray-100 flex w-1/2 cursor-pointer items-center mt-4 transition duration-100 transform hover:scale-105">
                    <div class="rounded overflow-hidden w-36 m-2 flex-none">
                        <img v-if="product.image" :src=" 'http://localhost:1337' + product.image.formats.thumbnail.url">
                    </div>
                    <div>
                        <div class="text-3xl text-green-900 font-semibold ml-4">
                            {{ product.name }}
                        </div>
                        <div class="text-xl text-green-900 ml-4">
                            {{ product.price }} €
                        </div>
                        <div class=" flex ml-4 mt-4">
                            <div>
                                <button class="rounded bg-red-600 transition-all duration-150 ease-linear hover:bg-red-500 text-white text-l p-2" @click=supprimerProduit(product.id)>Supprimer le produit</button>
                            </div>
                            <div class="ml-2 mt-2">
                                <nuxt-link :to="`modif/${product.id}`" class="rounded bg-green-900 transition-all duration-150 ease-linear hover:bg-green-800 text-white text-l p-2">Modifier le produit</nuxt-link>
                            </div>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
        <div class="mt-10">.</div>
    </div>
</template>

<script>
export default {
    data() {
        return {
           items: []
        }
    },
    created() {
        this.chargerProduits();
    },
    methods: {
        chargerProduits() {
            this.$axios.$get('products').then((response) => {
                this.items = response;
            });
        },
        supprimerProduit(id) {
            this.$axios.$delete('products/' + id).then(() => {
                const found = this.items.find((item) => item.id === id);
                const index = this.items.indexOf(found);
                this.items.splice(index, 1);
                this.$router.push('/produits');
            });
        },
    },
}
</script>