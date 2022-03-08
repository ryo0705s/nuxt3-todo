<template>
  <div>
    <input v-model="todo" />
    <button @click="add">追加</button>
    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index">
        {{ todo }}
        <button
          class="status"
          @click="checkStatus(index)"
          v-if="index === currentIndex"
        >
          {{ status }}
        </button>
        <button class="status" @click="checkStatus(index)" v-else>
          未着手
        </button>
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
      statusList: ["着手中", "完遂", "未着手"],
      status: "未着手",
      currentIndex: "",
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
    checkStatus(index) {
      let current = this.status;
      this.status = this.statusList.splice(0, 1).join("");
      this.statusList.push(this.status);
      this.currentIndex = index;
    },
  },
  // watch: {
  //   editTarget(newVal, oldVal) {
  //     // return newVal;
  //     console.log(newVal, oldVal);
  //   },
  // },
};
</script>
<style scoped>
li {
  list-style: none;
}
.status {
  background-color: #aae7aa;
}
</style>
