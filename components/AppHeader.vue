<template>
    <div class="bg-gray-100 text-green-900 fixed font-semibold w-full top-0 py-3 flex z-10">
        <div class="container ml-10 flex items-center justify-start text-4xl italic text-green-900 font-serif">
            La patisserie Luco
        </div>
        <div class="container mx-auto flex items-center justify-end">
            <nav class="flex items-center">
                <nuxt-link to="/" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Accueil</nuxt-link>
                <nuxt-link to="/produits" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Produits</nuxt-link>
                <nuxt-link to="/informations" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline inline">Informations</nuxt-link>
                <nuxt-link v-if="!isAuthenticated" to="/connexion" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Connexion</nuxt-link>
                <nuxt-link v-if="!isAuthenticated" to="/inscription" class="hidden xl:block font-abhaya-libre uppercase text-green-900 tracking-wider px-4 xl:px-8 py-2 text-lg hover:underline">Inscription</nuxt-link>
                
                <div v-if="isAuthenticated" @click=showLogout() class="relative" x-data="{ open: true }">
                    <button @click="open = !open" class="flex flex-row text-gray-900 bg-gray-200 items-center px-4 py-2 mt-2 text-sm font-semibold text-left bg-transparent rounded-lg dark-mode:bg-transparent dark-mode:focus:text-white dark-mode:hover:text-white dark-mode:focus:bg-gray-600 dark-mode:hover:bg-gray-600 md:w-auto md:inline md:mt-0 md:ml-4 hover:text-gray-900 focus:text-gray-900 hover:bg-gray-200 focus:bg-gray-200 focus:outline-none focus:shadow-outline">
                        <span>{{ loggedInUser.username }}</span>
                        <svg fill="currentColor" viewBox="0 0 20 20" :class="{'rotate-180': open, 'rotate-0': !open}" class="inline w-4 h-4 mt-1 ml-1 transition-transform duration-200 transform md:-mt-1"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                    </button>
                    <div v-if="show_logout" x-transition:enter="transition ease-out duration-100" x-transition:enter-start="transform opacity-0 scale-95" x-transition:enter-end="transform opacity-100 scale-100" x-transition:leave="transition ease-in duration-75" x-transition:leave-start="transform opacity-100 scale-100" x-transition:leave-end="transform opacity-0 scale-95" class="absolute right-0 mt-2 origin-top-right">
                        <div class="px-2 pt-2 pb-4 bg-white rounded-md shadow-lg w">
                        <a class="flex flex row items-start rounded-lg bg-transparent p-2 dark-mode:hover:bg-gray-600 dark-mode:focus:bg-gray-600 dark-mode:focus:text-white dark-mode:hover:text-white dark-mode:text-gray-200 hover:text-gray-900 focus:text-gray-900 hover:bg-gray-200 focus:bg-gray-200 focus:outline-none focus:shadow-outline" href="#">
                            <a class="navbar-item cursor-pointer" @click="logout">Déconnexion</a>
                        </a>
                        </div>
                    </div>
                </div> 
            </nav>
        </div>
    </div>
</template>

<script>
import { mapGetters } from "vuex";
export default {
    data() {
        return {
            show_logout: false
        }
    },
    computed: {
        ...mapGetters(["isAuthenticated", "loggedInUser"]),
    },
    methods: {
        async logout() {
            await this.$auth.logout()
        },
        showLogout() {
            this.show_logout = !this.show_logout;
        }
    },
    mounted() {
        // Get all "navbar-burger" elements
        const $navbarBurgers = Array.prototype.slice.call(
            document.querySelectorAll(".navbar-burger"),
            0
        );
        // Check if there are any navbar burgers
        if ($navbarBurgers.length > 0) {
            // Add a click event on each of them
            $navbarBurgers.forEach((el) => {
            el.addEventListener("click", () => {
                // Get the target from the "data-target" attribute
                const target = el.dataset.target;
                const $target = document.getElementById(target);
                // Toggle the "is-active" class on both the "navbar-burger" and the "navbar-menu"
                el.classList.toggle("is-active");
                $target.classList.toggle("is-active");
                });
            });
        }
    }
}
</script>