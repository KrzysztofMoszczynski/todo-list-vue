<template>
  <h1>{{ title }}</h1>
  <ul id="todolist">
    <li v-for="(item, index) in todos" :key="item">
      <button class="btn" @click="handleDelete(index)">
        <i class="fa fa-trash"></i>
      </button>
      {{ item }}
    </li>
  </ul>
  <input type="text" ref="newThing" />
  <button @click="handleAdd">Add</button>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      title: 'Todo list',
      todos: [],
    };
  },
  methods: {
    handleAdd() {
      if (this.$refs.newThing.value.length > 0) {
        console.log(this.$refs.newThing.value);
        this.todos.push(this.$refs.newThing.value);
        this.$refs.newThing.value = '';
        console.log(this.todos[0]);
      }
    },
    handleDelete(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  padding-left: 40px;
}
</style>
