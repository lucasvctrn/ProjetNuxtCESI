<template>
    <div class="p-0 sm:p-12 h-screen">
        <div class="mx-auto max-w-md px-6 py-12 bg-white border-0 shadow-lg sm:rounded-3xl">
            <h1 class="text-2xl font-bold mb-8">Connexion</h1>
            <Notification v-if="error" type="danger" :message="error" />
            <form method="post" @submit.prevent="login">

                <div>
                    <label class="text-green-900">Entrez votre adresse email</label>
                </div>

                <div class="relative z-0 w-full mb-5">
                    <input
                    v-model="email"
                    type="email"
                    name="email"
                    placeholder="Email"
                    class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
                    />
                </div>

                <div>
                    <label class="text-green-900">Entrez votre mot de passe</label>
                </div>

                <div class="relative z-0 w-full mb-5">
                    <input
                    v-model="password"
                    type="password"
                    name="password"
                    placeholder="Mot de passe"
                    required
                    class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
                    />
                </div>

                <button 
                    id="button"
                    type="submit"
                    class="w-full px-6 py-3 mt-3 text-lg text-white transition-all duration-150 ease-linear rounded-lg shadow outline-none bg-green-900 hover:bg-green-800 hover:shadow-lg focus:outline-none"
                >
                    Se connecter
                </button>
            </form>
        </div>
    </div>
</template>

<script>
import Notification from "~/components/Notification";

export default {
    components: {
        Notification,
    },
    data() {
        return {
            email: "",
            password: "",
            error: null,
        };
    },
    methods: {
        async login() {
            this.error = null;
            try {
                await this.$auth.loginWith("local", {
                    data: {
                        identifier: this.email,
                        password: this.password,
                    },
                });
                this.$router.push("/");
            } catch (e) {
                this.error = e.response.data.message[0].messages[0].message;
            }
        },
    },
};
</script>