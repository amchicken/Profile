<template>
    <img :src="require(`../assets/logo/${name}.svg`)" style="width: 250px;height: 250px;">
</template>

<script>
export default {
    props: {
        name: String
    },
    
    data() {
        return {
        }
    },

    computed() {
    }
}
</script>

<style>
    img {
        padding: 10px;
    }
</style>