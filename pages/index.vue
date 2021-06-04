<template>
  <div class="bg-center overflow-hidden">
    <main class="bg-white font-abhaya-libre relative">
      <div class="container mx-auto px-6 sm:px-12 flex flex-col sm:flex-row items-center relative bg-cover" style="background-image: url('~assets/boutique.png')">
          <div class="sm:w-1/2 xl:w-2/6 flex flex-col items-start py-24 sm:py-0">
              <h1 class="text-6xl xl:text-10xl font-abhaya-libre text-green-900 font-bold leading-none">La Gourmandise.</h1>
              <h2 class="text-xl xl:text-3xl font-abhaya-libre text-green-900 uppercase font-bold leading-none tracking-widest mt-2 mb-6">Le plus pur des péchés.</h2>
              <p class="xl:text-lg tracking-wider text-gray-700 font-alegraya-sans">Découvrez notre large gamme de pâtisseries et viennoiseries toutes plus colorées et originales les unes que les autres.</p>
              <nuxt-link to="/produits" class="font-montserrat text-white sm:font-xl uppercase py-3 px-6 sm:py-4 sm:px-8 rounded-full shadow-lg bg-green-900 hover:bg-green-800 mt-8 sm:mt-16">Voir les produits</nuxt-link>
          </div>
          <div class="ml-10 rounded overflow-hidden w-4/5 flex-none">
              <img src="~/assets/boutique.jpg" />
          </div>
        </div>
    </main>
  </div>
</template>

<script>
export default {}
</script>