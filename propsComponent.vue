<template>
  <div>{{ val }}</div>
  <!-- <div>"hoge"</div> -->
</template>
<script>
export default {
  // props: {
  //   hoge1: {
  //     type: String,
  //     default: "ssss",
  //     required: true,
  //   },
  //   hoge2: {
  //     type: String,
  //     default: "ss",
  //     required: false,
  //   },
  // },
  // props: ["hoge1", "hoge2"],
  name: "Hoge",
  props: ["val"],
};
</script>
