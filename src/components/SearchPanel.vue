<template>
  <input
    :value="modelValue"
    type="text"
    class="search-panel form-control"
    placeholder="Find a task"
    @input="onUpdateSearch"
  />
</template>

<script>
export default {
  props: {
    modelValue: {
      type: String,
    },
  },
  methods: {
    onUpdateSearch(event) {
      this.$emit('update:modelValue', event.target.value)
    },
  },
}
</script>

<style lang="scss" scoped>
.search-panel {
  margin-bottom: 15px;
  padding: 10px 12px;
  border-radius: 30px;
  border: none;
  background-color: #e6f0ff;
  box-shadow: 15px 15px 30px rgba(0, 0, 0, 0.1);
  &:focus {
    box-shadow: 15px 15px 30px rgba(0, 0, 0, 0.1);
    outline: 3px solid #e6f0ff;
  }
}
</style>
