<template>
  <transition-group
    name="list"
    tag="div"
    class="list"
  >
    <transition-group
      name="list"
      tag="div"
      v-if="data.length > 0"
    >
      <todo-list-item
        v-for="item in data"
        :key="item.id"
        :item="item"
        @remove="$emit('remove', item)"
      />
    </transition-group>

    <h2
      v-else
      class="list-empty"
    >
      Todo list is empty.
    </h2>
  </transition-group>
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
  min-height: 20vh;
  &-empty {
    text-align: center;
    color: rgba(255, 0, 0, 0.5);
    font-size: 25px;
  }
  &-enter-active,
  &-leave-active {
    transition: all 0.4s ease;
  }
  &-enter-from,
  &-leave-to {
    opacity: 0;
    transform: translateY(20px);
  }
  &-move {
    transition: transform 0.4s ease;
  }
}
</style>
