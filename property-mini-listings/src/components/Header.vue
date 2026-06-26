<template>
  <header class="header">
    <h1>Elijah's Properties</h1>
    <p>Total Properties: {{ count }}</p>
  </header>
</template>

<script>
export default {
  props: {
    count: Number
  }
}
</script>

<style scoped>
.header {
  text-align: center;
  padding: 20px;
  background: crimson;
  color: white;
}
</style>