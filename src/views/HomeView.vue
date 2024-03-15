<template>
  <div class="container">
    <HeaderSigma :showAddTask="showAddTask" @toggle-add-task="toggleAddTask" title="Task Tracker ✅"/>
    <div v-if="showAddTask">
      <AddTaskSigma @add-task="addTask"/>
    </div>
    <TasksSigma @toggle-reminder="toggleReminder" @delete-task= "deleteTask" v-bind:tasks="tasks"/>
  </div>
</template>

<script>
import HeaderSigma from '../components/HeaderSigma.vue';
import TasksSigma from '../components/TasksSigma.vue';
import AddTaskSigma from '../components/AddTaskSigma.vue';


export default {
  name: 'HomeView',
  components: {
    HeaderSigma,
    TasksSigma,
    AddTaskSigma,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    },
    async addTask(task) {
      const res = await fetch('http://localhost:5000/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task),
      })

      const data = await res.json()
      this.tasks = [...this.tasks, data];
    },
    async deleteTask(id) {
      if (confirm('Are you sure?')) {
        const res = await fetch(`http://localhost:5000/tasks/${id}`, {
          method: 'DELETE',
        })

        res.status === 200 ? (this.tasks = this.tasks.filter((task) => task.id !== id)) : alert('Error deleting task')
        
      }
    }, 
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      const updTask = {...taskToToggle, reminder: !taskToToggle.reminder}
      const res = await fetch(`http://localhost:5000/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updTask),
      })
      
      const data = await res.json()
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: data.reminder} : task)
    },
    async fetchTask(id) {
      const res = await fetch(`http://localhost:5000/tasks/${id}`);

      const data = await res.json();

      return data;
    },
    async fetchTasks() {
      const res = await fetch('http://localhost:5000/tasks');

      const data = await res.json();

      return data;
    },
  },
  async created() {
    this.tasks = await this.fetchTasks()
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  margin: 30px auto;
  min-width: 440px;
  overflow: auto;
  min-height: 670px;
  border: 1px solid #afbdb3;
  padding-top: 30px;
  padding-left: 30px;
  padding-right: 30px;
  padding-bottom: 30px;
  border-radius: 5px;
  margin-bottom: 70px;

}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
