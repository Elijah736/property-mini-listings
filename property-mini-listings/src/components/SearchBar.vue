<template>
  <input
    type="text"
    placeholder="Search by title or location"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  props: ['modelValue']
}
</script>

<style scoped>
input {
  padding: 10px;
  width: 200px;
  border-radius: 5px;
}
</style>