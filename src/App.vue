<template>
  <div id="app">
    <h1>Crear una nueva tarea</h1>

    <form @submit.prevent="addNewTask()">
      <label>Tarea </label>
      <input type="text" placeholder="Ingresa una tarea nueva" v-model="newTasks">
      <button type="submit">Crear</button>
    </form>
    <h2>Lista</h2>
    <div>
      <ul v-for="(task, i) in tasks" :key="i">
        <li>
          {{ i+1 }}: {{task}}
          <button @click="deleteTask(i)">Borrar</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        newTasks: '',
        tasks: [],
      };
    },
    methods: {
      addNewTask() {
        this.tasks.push(this.newTasks)
        this.newTasks = ''
      },
      deleteTask(someTask){
        this.tasks.splice(someTask, 1)
      }
    },
  }
</script>

<style>
*{
  text-align: center;
}
</style>