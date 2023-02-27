<template>
  <form
    @submit.prevent
    class="add-form d-flex"
  >
    <input
      v-model="task.label"
      type="text"
      class="add-form__input form-control"
      placeholder="Add task"
      required
    />

    <button
      type="submit"
      class="btn btn-add-form"
      @click="createTask"
    >
      <i class="add-form__circle fas fa-plus-circle"></i>
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      task: {
        label: '',
        done: false,
        important: false,
      },
    }
  },
  methods: {
    createTask() {
      if (this.task.label) {
        this.task.id = Date.now()

        this.$emit('create', this.task)
        this.task = {
          label: '',
          done: false,
          important: false,
        }
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.add-form {
  button {
    position: relative;
  }
  &__input {
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
  &__circle {
    top: -5px;
    left: -20px;
    position: absolute;
    font-size: 55px;
    color: #0d6efd;
    border-radius: 50%;
    transition: 0.5s all;
    box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.5);
    &:hover {
      box-shadow: 0 0 15px rgba(13, 110, 253, 1);
    }
  }
}
</style>
