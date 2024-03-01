<template>
    <div v-for="task in tasks" :key="task.id">
        <TaskSigma @delete-task="$emit('delete-task', task.id)" :task="task" />
        <div class="border"></div>

    </div>
</template>

<script>
import TaskSigma from './TaskSigma.vue';
export default {
    name: 'TasksSigma',
    components: {
        TaskSigma,
    },
    props: {
        tasks: Array
    },
    emits: ['delete-task']

}
</script>

<style scoped>
    @import url("https://fonts.googleapis.com/css2?family=Lato:wght@700&display=swap");

h3 {
    font-family: "Lato", sans-serif;
    font-weight: 700;
    font-style: normal;
    color: aquamarine;;
}

.border-bottom {
    border-bottom: 1px solid #ccc;
    margin-bottom: 10px;
}

</style>