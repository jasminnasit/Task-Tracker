<template>
  <div class="container">
    <Header title = "Task Tracker"/>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data() {
    return {
    tasks: []
    }
  },
  methods:{
    deleteTask(id){
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task)=> task.id !== id )
      }
    },

    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder:!task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctor Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'School Appointment',
        day: 'March 3rd at 1:30pm',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.btn {
  background-color: #4CAF50; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.container{
  padding: 20px;
}
</style>
