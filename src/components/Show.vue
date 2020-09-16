<template>
  <div class="float-right">
    <p>{{todo.description}}</p>
    <button @click="$emit('close')">Close</button>
  </div>
</template>
<script>
export default {
  name: "Show",
  props: ["todo"],
};
</script>