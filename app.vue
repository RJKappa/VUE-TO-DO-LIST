<template>
  <div class="container">
    <h1>Todo List</h1>
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" placeholder="Add new todo">
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <span>{{ todo }}</span>
        <button @click="removeTodo(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo.trim());
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.container {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 5px solid #000000;
  border-radius: 10px;
}

input[type="text"] {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 5px solid #000000;
  border-radius: 1px;
}

ul{
  list-style-type: none;
  padding: 0;
}

li{
  margin-bottom: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li button {
  margin-left: 10px;
  padding: 3px 5px;
  border: 3px solid #000000;
}
</style>