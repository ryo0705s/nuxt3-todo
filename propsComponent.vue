<template>
  <div>
    <!-- <div>{{ val }}</div> -->
    <!-- <p>child_num: {{ child_num }}</p>
    <button @click="send">"親に値を渡す"</button> -->
    <p>name:<slot name="hehe"> sasaki ryo</slot></p>
    <p>adress:<slot name="fufu"> glory</slot></p>
  </div>
</template>
<script>
export default {
  // props: {
  //   val: {
  //     type: String,
  //     default: "ddddddd",
  //   },
  // },
  // data() {
  //   return {
  //     child_num: 0,
  //   };
  // },
  // methods: {
  //   send() {
  //     this.$emit("my-click", this.child_num);
  //   },
  // },
  // name: "Hoge",
  // props: ["val"],
};
</script>
