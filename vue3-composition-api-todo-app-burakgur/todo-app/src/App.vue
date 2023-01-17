<script setup>
import { ref } from 'vue'
let listTodo = ref([])
let newTodo = ref('')

const addTodo = () => {
  listTodo.value.push({name: newTodo.value})
  newTodo = ref('')
}

const actRemove = (todo) => {
  listTodo.value = listTodo.value.filter(self => self !== todo)
}

</script>

<template>
  <main class="app">

    <div class="header">
      <h1 class="title">ToDo App</h1>
    </div>

    <div class="create-todo">
      <form @submit.prevent="addTodo">
        <h4>New ToDo</h4>
        <input type="text"
              v-model="newTodo"
        >
        <br>
        <button type="submit">Add ToDo</button>
      </form>
    </div>

    <div class="todo-list">
      <h2>
        ToDo List
      </h2>
      <div v-if="listTodo.length > 0">
          <div  v-for="todo in listTodo" v-bind:key="todo.name"  class="todo">
            <p>{{todo.name}}</p>
            <button @click="actRemove(todo)" class="remove">Remove</button>
          </div>
      </div>
      <div v-else class="empty">
        <h4>Empty List</h4>
      </div>

      <!-- <div class="todo">
        <p>Eat</p>
        <button class="remove">Remove</button>
      </div> -->
    </div>
  </main>
</template>

<style scoped>
.app {
  height: 100vh;
  display: flex;
  align-items: center;
  flex-direction: column;
  margin-top: 3%;
}

.title {
  margin-bottom: 8%;
  color: white;
}

.create-todo form {
  width: 70vh;
  color: white;
}

.create-todo form input {
  height: 40px;
  width: 70vh;
  border-radius: 5px;
  margin: 5px auto;
  border: 1px solid #727476;
  padding: 12px 20px;
  font-size: 18px;
  color: white;
}

.create-todo form button {
  height: 40px;
  width: 70vh;
  border-radius: 5px;
  border: none;
  background-color: #A0A4D9;
  font-weight: 700;
  margin-bottom: 25px;
}

.todo-list {
  width: 70vh;
  color: white;
}
.todo-list h2{
  padding-bottom: 10px;
  border-bottom: 2px solid #727476;
}
.todo {
  display: flex;
  width: 67vh;
  margin: 0 auto;
  margin-top: 10px;
  justify-content: space-between;
  align-items: center;
  padding: 8px 30px;
  border-radius: 10px;
  border: 1px solid #727476;
}

.todo button {
  padding: 5px 8px;
  border-radius: 5px;
  background-color: #A0A4D9;
  border: none;
  font-weight: 700;
}

.empty {
  color: #727476;
  text-align: center;
  margin-top: 5%;
}
</style>
