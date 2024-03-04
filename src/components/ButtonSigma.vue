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
            this.$emit('toggle-add-task')
        }
    }}
</script>

<style>

</style>