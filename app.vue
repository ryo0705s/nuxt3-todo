<template>
  <div>
    <input v-model="todo" />
    <button @click="add">追加</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="remove(index)">削除</button>
        <button @click="edit(index)">編集</button>
        <input v-model="newTodo" v-show="target" />
        <button @click="edited(index)" v-show="target">更新</button>
        <!-- <div v-show="target">target</div> -->
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
      target: false,
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
      this.target = true;
    },
    edited(index) {
      this.todos.splice(index, 1, this.newTodo);
      this.target = false;
    },
  },
};
</script>
