<template>
  <p>{{todo.description}}</p>
</template>
<script>
export default {
  name: "Show",
  props: ["todo"],
};
</script>