<template>
  <div>
    <span>Completed Tasks: {{ todos.filter(todo => {return todo.done === true}).length }}</span>
    <br>
    <span>Pending Tasks: {{ todos.filter(todo => {return todo.done === false}).length }}</span>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" :key="todo.id" v-bind:todo="todo"></todo>
	</div>
</template>

<script>
  import Todo from './Todo';

  export default {
    props: ['todos'],
    components: {
      Todo,
    },
    methods: {
      deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos[todoIndex].done = true;
      }
    },
  }
</script>

<style>

</style>