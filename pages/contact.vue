<template>
    <div class="p-0 sm:p-12">
    <div class="mx-auto max-w-md px-6 py-12 bg-white border-0 shadow-lg sm:rounded-3xl">
        <h1 class="text-2xl font-bold mb-8">Commander ou demander des informations</h1>
        <form id="form" novalidate>

        <div>
            <label for="name" class="text-green-900">Entrez votre nom</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="text"
            name="name"
            placeholder=" "
            required
            class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <div>
            <label for="name" class="text-green-900">Entrez votre adresse email</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="email"
            name="email"
            placeholder=" "
            class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <div>
            <label for="name" class="text-green-900">Entrez votre message</label>
        </div>

        <div class="relative z-0 w-full mb-5">
            <input
            type="text"
            name="name"
            placeholder=" "
            required
            class="pt-3 pb-2 block w-full px-0 mt-0 bg-transparent border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-black border-gray-200"
            />
        </div>

        <button
            id="button"
            type="button"
            class="w-full px-6 py-3 mt-3 text-lg text-white transition-all duration-150 ease-linear rounded-lg shadow outline-none bg-green-900 hover:bg-green-800 hover:shadow-lg focus:outline-none"
        >
            Envoyer
        </button>
        </form>
    </div>
    </div>
</template>

<script>

</script>