<template>
    <div>
        <pre>
            {{ plat }}
        </pre>
    </div>
</template>

<script>
export default {
    data() {
        return {
            plat: null
        }
    },
    created() {
        const id = this.$route.params.id;
        this.$axios.$get(`products/${id}`).then((response) => {
            this.plat = response;
        })
    }
}
</script>