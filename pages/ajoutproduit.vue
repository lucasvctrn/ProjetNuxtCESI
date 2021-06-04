<template>
    <div class="p-0 sm:p-12">
    <div class="mx-auto max-w-md px-6 py-12 bg-white border-0 shadow-lg sm:rounded-3xl">
        <h1 class="text-2xl font-bold mb-8">Ajouter un produit</h1>
        <form id="form" novalidate>

        <div>
            <label class="text-green-900">Choississez la catégorie du produit</label>
        </div>

        <fieldset class="relative z-0 w-full p-px mb-5">
            <div class="block pt-3 pb-2 space-x-4">
            <label>
                <input
                type="radio"
                name="radio"
                id="patisserie"
                value="1"
                class="mr-2 text-black border-2 border-gray-300 focus:border-gray-300 focus:ring-black"
                />
                Patisserie
            </label>
            <label>
                <input
                type="radio"
                name="radio"
                id="viennoiserie"
                value="2"
                class="mr-2 text-black border-2 border-gray-300 focus:border-gray-300 focus:ring-black"
                />
                Viennoiserie
            </label>
            </div>
        </fieldset>

        <div>
            <label class="text-green-900">Entrez le nom de votre produit</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="text"
            id="name"
            placeholder=" "
            required
            class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <div>
            <label class="text-green-900">Entrez le prix de votre produit</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="number"
            id="price"
            placeholder=" "
            class="pt-3 pb-2 pl-5 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <div>
            <label class="text-green-900">Entrez une description de votre produit</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="text"
            id="description"
            placeholder=" "
            required
            class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <div>
            <label class="text-green-900">Ajoutez une photo</label>
        </div>

        <div class="grid grid-cols-1 mt-5 mx-7">
            <div class='flex items-center justify-center w-full'>
                <label class='flex flex-col border-4 border-gray-300 border-dashed w-full h-32 hover:bg-gray-100 hover:border-green-900 group'>
                    <div class='flex flex-col items-center justify-center pt-7'>
                    <svg class="w-10 h-10 text-green-800 group-hover:text-green-900" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                    <p class='lowercase text-sm text-green-900 group-hover:text-green-900 pt-1 tracking-wider'>Sélectionner une photo</p>
                    </div>
                <input type='file' class="hidden" />
                </label>
            </div>
        </div>

        <button
            id="button"
            type="button"
            class="w-full px-6 py-3 mt-3 text-lg text-white transition-all duration-150 ease-linear rounded-lg shadow outline-none bg-green-900 hover:bg-green-800 hover:shadow-lg focus:outline-none"
            @click=ajouterProduit()
        >
            Créer le produit
        </button>
        </form>
    </div>
    </div>
</template>


<script>
export default {
    data() {  
        return { 
            name: "",
            category: "",
            price: "",
            description: "",
        }
    },
    methods: {
        ajouterProduit() {
        this.$axios.$post('products', {
            name: document.getElementById("name").value,
            category: this.getCategory(),
            price: document.getElementById("price").value,
            description: document.getElementById("description").value
        }).then((response) => {
            this.$router.push('/produits');
        });
        },
        getCategory(){
            if (document.getElementById('patisserie').checked) {
                return "patisserie";
            }
            if (document.getElementById('viennoiserie').checked) {
                return "viennoiserie";
            }
        }
    },
}
</script>