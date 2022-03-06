<template>
  <div>
    <input v-model="todo" />
    <button @click="add">追加</button>
    <ul>
      <li v-for="(status, id) in statusList" :key="id" class="status">
        <button @click="checkStatus(id)">{{ status }}</button>
      </li>
    </ul>
    <br />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}<button>{{ status }}</button>
        <button @click="remove(index)">削除</button>
        <button @click="edit(index)">編集</button>
      </li>
    </ul>
    <div v-show="target && editTarget !== ''">
      <input v-model="newTodo" />
      <button @click="edited">更新</button>
    </div>
    <div v-show="target && editTarget === ''"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      statusList: ["未着手", "着手中", "完遂"],
      status: "未着手",
      currentStatus: "",
      todo: "",
      todos: [],
      newTodo: "",
      target: false,
      editTarget: "",
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
      this.editTarget = index;
    },
    edited() {
      this.todos.splice(this.editTarget, 1, this.newTodo);
      this.target = false;
    },
    checkStatus(id) {
      let current = this.statusList[id];
      this.status = current;
      console.log(current, id, "今何？");
    },
  },
};
</script>
<style scoped>
li {
  list-style: none;
}
.status {
  float: left;
}
</style>
