<template>
    <div class="bg-gray-100 text-green-900 fixed font-semibold w-full top-0 py-3 flex z-10">
        <div class="container ml-10 flex items-center justify-start text-4xl italic text-green-900 font-serif">
            La patisserie Luco
        </div>
        <div class="container mx-auto flex items-center justify-end">
            <nav class="flex items-center">
                <nuxt-link to="/" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Accueil</nuxt-link>
                <nuxt-link to="/produits" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Produits</nuxt-link>
                <nuxt-link to="/apropos" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">A Propos</nuxt-link>
                <nuxt-link to="/contact" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Contact</nuxt-link>
            </nav>
        </div>
    </div>
</template>
