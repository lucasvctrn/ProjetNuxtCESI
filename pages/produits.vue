<template>
    <div class="text-left mt-16">
        <div v-for="product in items">
            <div class="flex items-center mb-2 container justify-center">
                <div class="bg-gray-200 rounded overflow-hidden w-20 flex-none">
                    <img v-if="product.image" :src=" 'http://localhost:1337' + product.image.formats.thumbnail.url">
                </div>
                <div class="text-xl font-semibold ml-4">
                    <nuxt-link :to="`products/${product.id}`">
                        {{ product.name }}
                    </nuxt-link>
                </div>
                <div class="items-end">
                    <button class="p-1 rounded bg-red-500 text-gray-50 " @click=supprimerProduit(product.id)>X</button>
                </div>
            </div>
        </div>
        <div>
            <button class="p-2 rounded bg-blue-500 text-gray-50" @click=ajouterProduit()>Ajouter un produit</button>
        </div>
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
    ajouterProduit() {
      this.$axios.$post('product', {
        name: 'Tiramisu',
        category: 'patisserie'
      }).then((response) => {
        this.items.push(response);
      });
    },
    supprimerProduit(id) {
      this.$axios.$delete('products/' + id).then(() => {
        const found = this.items.find((item) => item.id === id);
        const index = this.items.indexOf(found);
        this.items.splice(index, 1);
      });
    },
  },
}
</script>