<template>
  <div>
    <input v-model="todo" />
    <button @click="add">追加</button>
    <Hoge></Hoge>
    <Hoge><template v-slot:hehe> 佐々木良 </template></Hoge>
    <Hoge><template v-slot:fufu> グローリー </template></Hoge>
    <!-- <Hoge v-bind:val="postItem"></Hoge> -->
    <!-- <Hoge val="fffff" /> -->
    <!-- <p>parent_num: {{ parent_num }}</p>
    <Hoge @my-click="childValue" /> -->
    <!-- <Hoge @my-click="parent_num = $event" /> -->
    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index">
        {{ todo.content }}
        <button
          class="status"
          @click="checkStatus(index)"
          v-if="todo.status != undefined"
        >
          {{ todo.status }}
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
    <v-menu>
      <template v-slot:activator="{ on }">
        <v-btn v-on="on">open</v-btn>
      </template>
      <v-list>
        <v-list-item> </v-list-item>
      </v-list>
    </v-menu>
  </div>
</template>
<script>
import Hoge from "./propsComponent";
export default {
  // name: "App",
  components: {
    Hoge,
    // Child,
  },
  data() {
    return {
      statusList: ["着手中", "完遂", "未着手"],
      currentIndex: "",
      todo: "",
      todos: [],
      newTodo: "",
      target: false,
      editTarget: "",
      // postItem: "d",
      // parent_num: 100,
    };
  },
  methods: {
    add() {
      this.todos.push({ content: this.todo, status: this.todos.status });
      this.todo = "";
    },
    remove(index) {
      this.todos.splice(index, 1);
    },
    edit(index) {
      this.newTodo = this.todos[index].content;
      this.target = true;
      this.editTarget = index;
    },
    edited() {
      this.todos.splice(this.editTarget, 1, {
        content: this.newTodo,
        status: this.todos.status,
      });
      this.target = false;
    },
    checkStatus(index) {
      let current = this.todos[index].status;
      this.todos[index].status = this.statusList.splice(0, 1).join("");
      this.statusList.push(this.todos[index].status);
      this.currentIndex = index;
    },
    // childValue(value) {
    //   this.parent_num = value;
    // },
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
