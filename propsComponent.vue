<template>
  <div>{{ val }}</div>
</template>
<script>
export default {
  props: {
    val: {
      type: String,
      default: "ddddddd",
    },
  },
  // name: "Hoge",
  // props: ["val"],
};
</script>
