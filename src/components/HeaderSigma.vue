<template>
    <header>
        <h1 class="title inter">{{title}}</h1>
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
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
    }
.title {
    font-size: 32px;
    text-align: center;
    padding-right: 15px;
    }
.archivo-black-regular {
    font-family: "Archivo Black", sans-serif;
    font-weight: 400;
    font-style: normal;
}
.inter {
    font-family: "Inter", sans-serif;
    font-optical-sizing: auto;
    font-weight: 700;
    font-style: normal;
    font-variation-settings:
    "slnt" 0;
}

ButtonSigma {
    padding-left: 30px;
}
</style>