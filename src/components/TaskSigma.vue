<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}
            <i @click="onDelete(task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>

    </div>
</template>

<script>
export default {
    name: 'TaskSigma',
    props: {
        task: {
            type: Object,
        //    required: true
        },
        //taskIndex: {
          //  type: Number,
            //required: true}
        },
    methods: {
        onDelete(id) {
            this.$emit('delete-task', id)
        }
    }
    }
</script>

<style scope>
@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css");

    .fas {
        font-size: 20px;
        color: #fcba03;
    }
    .fas:hover {
        color: red;
    }

    .task {
        background: #313438;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
        border-radius: 8px;
    }
    .task.reminder {
        border-left: 5px solid green;
    }
    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>