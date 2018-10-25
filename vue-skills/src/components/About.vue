<template>
    <div class="about">
        <h1> Hello {{ their_name }} - This is an about page</h1>
        <p>Lorem ipsum dolor dit amet, consectetur elit, sed do eiusdenod</p>
    </div>
</template>

<script>
export default {
    name: 'About',
    data() {
        return {
            their_name: this.$route.params.name
        }
    }
}
</script>