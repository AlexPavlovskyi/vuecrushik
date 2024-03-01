<template>
    <button @click="haveClicked()" :style="{ background: color}" class="btn">{{ text }}</button>
</template>

<script>
export default {
    name: 'ButtonSigma',
    props: {
        text: String,
        color: String,
},
    methods: {
        haveClicked() {
            console.log("haveClicked");
        }
    }}
</script>

<style>

</style>