<template>
  <div class="item-filter d-flex">
    <button
      :value="filter"
      :class="{
        'btn-filter__active': filter === button.name,
      }"
      class="btn"
      v-for="button of buttons"
      :key="button.name"
      type="button"
      @click="onFilterChange(button.name)"
    >
      {{ button.name }}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    filter: {
      type: String,
      required: true,
      default: 'all',
    },
  },
  data() {
    return {
      buttons: [{ name: 'all' }, { name: 'active' }, { name: 'done' }, { name: 'important' }],
    }
  },
  methods: {
    onFilterChange(name) {
      this.$emit('update:filter', name)
    },
  },
}
</script>

<style lang="scss" scoped>
.item-filter {
  margin: 0 5px 15px;
  justify-content: center;

  & button {
    height: 47px;
    max-width: 100%;
    font-size: 19px;
    border-radius: 0;
    color: #6c757d;
    text-shadow: 5px 5px 10px rgba(155, 152, 152, 0.3);
    transition: 0.3s all;
  }
  & button:active,
  & button:focus {
    /*outline: 0 !important;*/
    /*outline-color: transparent !important;*/
    /*outline-width: 0 !important;*/
    /*outline-style: none !important;*/
    box-shadow: 0 0 0 0 rgba(0, 123, 255, 0) !important;
  }

  & .btn-filter__active {
    color: #6610f2;
    font-size: 22px;
    text-shadow: 5px 5px 10px rgba(102, 16, 242, 0.3);
  }
}
</style>
