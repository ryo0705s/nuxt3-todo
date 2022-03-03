<template>
  <div>
    <input v-model="todo" />
    <button @click="add">追加</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="remove(index)">削除</button>
        <button @click="edit(index)">編集</button>
        <input v-model="newTodo" />
        <button @click="edited(index)">更新</button>
        <div v-show="target">target</div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      todo: "",
      todos: [],
      newTodo: "",
      target: true,
    };
  },
  methods: {
    add() {
      this.todos.push(this.todo);
      this.todo = "";
    },
    remove(index) {
      this.todos.splice(index, 1);
    },
    edit(index) {
      this.newTodo = this.todos[index];
      this.target = false;
    },
    edited(index) {
      this.todos.splice(index, 1, this.newTodo);
    },
  },
};
</script>
