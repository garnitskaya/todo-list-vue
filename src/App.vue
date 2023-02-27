<template>
  <div class="app">
    <app-header-info
      :allTasks="allTasks"
      :done="doneTasks"
      :percentWidth="percentWidth"
    />
    <search-panel v-model="searchQuery" />
    <item-filter v-model:filter="filter" />
    <todo-list
      :data="filteredAndSearchedItems"
      @remove="removeItem"
    />
    <item-add-form @create="createTask" />
  </div>
</template>

<script>
import AppHeaderInfo from './components/AppHeaderInfo'
import ItemAddForm from './components/ItemAddForm'
import ItemFilter from './components/ItemFilter'
import SearchPanel from './components/SearchPanel'
import TodoList from './components/TodoList'

export default {
  components: {
    AppHeaderInfo,
    SearchPanel,
    ItemFilter,
    TodoList,
    ItemAddForm,
  },
  data() {
    return {
      tasks: [
        { label: 'Купить машину', done: true, important: false, id: '1' },
        { label: 'Поехать на море ', done: false, important: true, id: '2' },
        {
          label: 'Пополнить интернет ',
          done: false,
          important: false,
          id: '3',
        },
      ],
      filter: 'all',
      searchQuery: '',
    }
  },
  methods: {
    createTask(task) {
      this.tasks.push(task)
    },
    removeItem(task) {
      this.tasks = this.tasks.filter((t) => t.id != task.id)
    },
  },
  computed: {
    allTasks() {
      return this.tasks.length
    },
    doneTasks() {
      return this.tasks.filter((item) => item.done).length
    },
    percentWidth() {
      return this.tasks.length ? ((this.doneTasks / this.tasks.length) * 100).toFixed(0) : 0
    },
    filterItem() {
      switch (this.filter) {
        case 'done':
          return this.tasks.filter((item) => item.done)
        case 'active':
          return this.tasks.filter((item) => !item.done)
        case 'important':
          return this.tasks.filter((item) => item.important)
        default:
          return this.tasks
      }
    },
    filteredAndSearchedItems() {
      if (this.searchQuery.length === 0) {
        return this.filterItem
      }

      return this.filterItem.filter((item) => item.label.toLowerCase().includes(this.searchQuery.toLowerCase()))
    },
  },
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  position: relative;
  padding: 25px;
  margin: 50px auto;
  max-width: 640px;
  color: #212529;
  box-shadow: 5px 5px 30px rgb(0 0 0 / 10%);
  border-radius: 5px;
  font-family: -apple-system, 'Roboto', sans-serif;
}
@media (max-width: 570px) {
  .app {
    padding: 0;
    margin: 10px;
    box-shadow: none;
  }
}
</style>
