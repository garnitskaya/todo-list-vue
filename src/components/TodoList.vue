<template>
  <div
    class="list"
    v-if="data.length > 0"
  >
    <todo-list-item
      v-for="item in data"
      :key="item.id"
      :item="item"
      @remove="$emit('remove', item)"
      v-model:done="item.done"
      v-model:important="item.important"
    />
  </div>
  <h2
    v-else
    class="list-empty"
  >
    Todo list is empty.
  </h2>
</template>

<script>
import TodoListItem from './TodoListItem'
export default {
  components: { TodoListItem },
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.list {
  margin-bottom: 40px;
  &-empty {
    text-align: center;
    color: rgba(255, 0, 0, 0.5);
    font-size: 25px;
  }
}
</style>
