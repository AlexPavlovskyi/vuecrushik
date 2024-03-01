<template>
    <header>
        <h1 class="title">{{title}}</h1>
        <ButtonSigma text="Add Task" color="#42f572"/>
    </header>
</template>

<script>
import ButtonSigma from './ButtonSigma.vue';

export default {
    name: "HeaderSigma",
    components: {
        ButtonSigma,
    },
    props: ['title'],
}
</script>

<style scoped>

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    }
.title {
    font-size: 36px;
    color: white;
    font-weight: 900;
    text-align: center;
    padding-right: 15px;
    }
ButtonSigma {
    padding-left: 30px;
}
</style>