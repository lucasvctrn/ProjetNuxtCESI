<!-- <template>
    <div class="text-left mt-16">
        <div v-for="plat in items">
            <div class="flex items-center mb-2">
                <div class="bg-gray-200 rounded overflow-hidden w-20 flex-none">
                    <img v-if="plat.image" :src=" 'http://localhost:1337' + plat.image.formats.thumbnail.url">
                </div>
                <div class="text-xl font-semibold ml-4">
                    <nuxt-link :to="`plats/${plat.id}`">
                        {{ plat.name }}
                    </nuxt-link>
                </div>
                <div class="items-end">
                    <button class="p-1 rounded bg-red-500 text-gray-50 " @click=supprimerPlat(plat.id)>X</button>
                </div>
            </div>
        </div>
        <div>
            <button class="p-2 rounded bg-blue-500 text-gray-50" @click=ajouterPlat()>Ajouter un plat</button>
        </div>
    </div>
</template> -->

<template>
    <div class="">

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
    this.chargerPlats();
  },
  methods: {
    chargerPlats() {
      this.$axios.$get('plats').then((response) => {
        this.items = response;
      });
    },
    ajouterPlat() {
      this.$axios.$post('plats', {
        name: 'Tiramisu',
        category: 'dessert'
      }).then((response) => {
        this.items.push(response);
      });
    },
    supprimerPlat(id) {
      this.$axios.$delete('plats/' + id).then(() => {
        const found = this.items.find((item) => item.id === id);
        const index = this.items.indexOf(found);
        this.items.splice(index, 1);
      });
    },
  },
}
</script>