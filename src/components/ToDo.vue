<template>
  <div>
    <h2>Vue.js To-Do List</h2>

    <!-- Input for adding new todo -->
    <div>
      <input type="text" v-model="newTodo" placeholder="Add new todo">
      <button @click="addTodo">Add</button>
    </div>

    <!-- List of todos -->
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <!-- Edit mode toggle -->
        <span v-if="editIndex !== index">
          {{ todo }}
          <button @click="editMode(index)">Edit</button>
        </span>
        
        <!-- Edit mode input -->
        <span v-else>
          <input type="text" v-model="todos[index]">
          <button @click="saveEdit(index)">Save</button>
        </span>

        <!-- Delete button -->
        <button @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      newTodo: '',
      editIndex: -1  // Track which todo is in edit mode
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo.trim());
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editMode(index) {
      this.editIndex = index;
    },
    /* eslint-disable-next-line */
    saveEdit(index) {
      // Save edited todo and exit edit mode
      this.editIndex = -1;
    }
  }
};
</script>

<style>
/* Add your styles here */
</style>
