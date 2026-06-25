<template>
  <select
    :value="modelValue"
    @change="$emit('update:modelValue', $event.target.value)"
  >
    <option value="">Sort Price</option>
    <option value="asc">Low to High</option>
    <option value="desc">High to Low</option>
  </select>
</template>

<script>
export default {
  props: ['modelValue']
}
</script>

<style scoped>
select {
  padding: 10px;
  border-radius: 5px;
}
</style>