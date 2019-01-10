<template>
  <div>

    <button @click="saveTBD">save</button>

    <BaseInput
      @keydown.enter='addTodo'
      v-model="newTodo"
    ></BaseInput>
    <ol v-if="todos.length">
      <BaseListItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo='todo'
        @remove='removeTodo'
      >
      </BaseListItem>
    </ol>
  </div>
</template>

<script>
import BaseInput from './BaseInput.vue';
import BaseListItem from './BaseListItem.vue';
let nextTodoId = 1;
export default {
  name: 'BaseList',
  components: {
    BaseInput, BaseListItem
  },
  data () {
    return {
      newTodo: '',
      todos: [],
    }
  },

  beforeMount () {
    let tbd = localStorage.getItem('tv-tbd')
    if (tbd) {
      this.todos = JSON.parse(tbd)
    } else {
      this.todos = []
    }
  },
  methods: {
    removeTodo (idToRemove) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== idToRemove;
      })
    },
    saveTBD () {
      localStorage.setItem('tv-tbd', JSON.stringify(this.todos))
    },

    addTodo () {
      const text = this.newTodo.trim()
      this.todos.push({
        id: nextTodoId++,
        text: text
      })
      this.newTodo = '';
    }
  },
}
</script>

<style scoped>
.bcontainer {
}
div button {
  position: absolute;
  right: 10px;
  top: 10px;
  bottom: 10px;
  width: 60px;
  height: 40px;
  background-color: hotpink;
  font-size: 20px;
  color: white;
  font-weight: bold;
  border-radius: 5px;
  border: none;
}
</style>