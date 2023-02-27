<template>
  <header class="app-header d-flex">
    <h1>All Tasks</h1>
    <div class="app-header__info">
      <span
        :style="{
          width: `${percentWidth}%`,
        }"
      ></span>
      <b>{{ done }}</b
      >of <b>{{ allTasks }}</b> tasks done
    </div>
  </header>
</template>

<script>
export default {
  props: {
    allTasks: {
      type: Number,
      required: true,
    },
    done: {
      type: Number,
      required: true,
    },
    percentWidth: {
      type: Number,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.app-header {
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
  & h1 {
    text-shadow: 5px 5px 10px rgba(155, 152, 152, 0.5);
  }
  &__info {
    position: relative;
    width: 300px;
    font-size: 17px;
    height: 27px;
    text-align: center;
    border: 1px solid #ffe866;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 10px 10px 30px rgba(0, 0, 0, 0.1);
    z-index: 1;
    & span {
      position: absolute;
      display: block;
      height: 100%;
      background-color: #ffe866;
      transition: 0.6s all;
      z-index: -1;
    }
  }
}
</style>
