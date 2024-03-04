<template>
    <header>
        <h1 class="title">{{title}}</h1>
        <ButtonSigma @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'"/>
    </header>
</template>

<script>
import ButtonSigma from './ButtonSigma.vue';

export default {
    name: "HeaderSigma",
    components: {
        ButtonSigma,
    },
    props: {
        title: String,
        showAddTask: Boolean,
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');


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
    font-family: 'Poppins', sans-serif;
    text-align: center;
    padding-right: 15px;
    }
ButtonSigma {
    padding-left: 30px;
}
</style>