<template>
  <div
    class="list-item d-flex"
    :class="{
      important: item.important,
      done: item.done,
    }"
  >
    <div class="list-item__box">
      <input
        class="list-item__check form-check-input"
        type="checkbox"
        v-model="item.done"
      />

      <span
        :title="item.label"
        :class="['list-item__text', { active }]"
        @click="active = !active"
      >
        {{ item.label }}
      </span>
    </div>

    <div class="list-item__buttons d-flex">
      <button
        class="btn btn-star"
        type="button"
        @click="item.important = !item.important"
      >
        <i class="star fas fa-star"></i>
      </button>

      <button
        class="btn btn-trash"
        type="button"
        @click="$emit('remove', item)"
      >
        <i class="trash fas fa-trash-alt"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      active: false,
    }
  },
}
</script>

<style lang="scss" scoped>
.list-item {
  padding: 10px 10px 10px 15px;
  margin-bottom: 20px;
  align-items: center;
  justify-content: space-between;
  background-color: #e9fcf6;
  box-shadow: 15px 15px 30px rgba(0, 0, 0, 0.1);
  border-radius: 30px;
  word-break: break-word;
  word-wrap: break-word;
  &__box {
    vertical-align: middle;
  }
  &__text {
    display: inline-block;
    height: 100%;
    font-size: 20px;
    vertical-align: middle;
    transition: 0.5s all;
    cursor: pointer;

    width: 440px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .active {
    height: 100%;
    white-space: unset;
    overflow: visible;
  }
  &__check {
    margin-right: 12px;
    border-radius: 50%;
    vertical-align: middle;
    border-color: rgba(32, 201, 151, 0.3);
    box-shadow: 0px 0px 10px rgba(32, 201, 151, 0.3);
    transition: 0.5s all;
    cursor: pointer;
  }

  &.important {
    .list-item__text {
      color: #ffd700;
      transition: 0.5s all;
    }
    .btn-star .star {
      color: #ffd700;
    }
  }

  &.done {
    background-color: #fbe9eb;

    .list-item__check:checked {
      background-color: rgb(255, 0, 0);
      border-color: rgb(255, 0, 0);
      box-shadow: 0px 0px 10px rgba(255, 0, 0, 1);
    }
    .list-item__text {
      color: #cecece;
      text-decoration: line-through;
      font-style: italic;
    }
  }

  .btn-trash .trash {
    font-size: 20px;
    color: #e5383b;
    transition: 1s all;

    &:hover,
    &:active {
      transform: rotate(720deg);
    }
  }

  .btn-star .star {
    font-size: 20px;
    color: rgba(32, 201, 151, 0.3);
    transition: 0.5s all;

    &:hover,
    &:active {
      transform: scale(1.2);
    }
  }
}
@media (max-width: 768px) {
  .list-item {
    &__text {
      width: 340px;
    }
  }
}
@media (max-width: 570px) {
  .list-item {
    &__text {
      width: 240px;
    }
  }
}
</style>
