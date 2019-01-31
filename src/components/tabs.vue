<template>
  <footer class="footer">
    <span class="todo-count">
      <!-- <strong>{{ todos.filter(item => !item.done).length }}</strong> item left</span> -->
      <!-- <strong>{{ getRemaining() }}</strong> item left</span> -->
      <strong>{{unFinishedTodoLength}}</strong> item left
    </span>

    <ul class="filters">
      <li v-for="state in states" :key="state">
        <a :class="filter === state ? 'selected' : ''" href="javaScripts:;" @click="toggleState(state)">{{state}}</a>
      </li>
      <!-- <li>
        <a :class="{selected: hash === '#/'}" href="#/">All</a>
      </li>
      <li>
        <a :class="{selected: hash === '#/active'}" href="#/active">Active</a>
      </li>
      <li>
        <a :class="{selected: hash === '#/completed'}" href="#/completed">Completed</a>
      </li> -->
    </ul>
    <button class="clear-completed" @click="clearAllDone">Clear completed</button>
  </footer>
</template>

<script>
export default {
   props: {
    todo: {
      type: Array,
      required: true
    },
    filter:{
      type:String,
      required:true
    }
  },
  data() {
    return {
      states:['all','active','completed']
    }
  },
  computed: {
    unFinishedTodoLength() {
      // todo数组未完成的个数 completed默认是false
      return this.todo.filter((todo)=>!todo.completed).length
    }
  },
  methods: {
    // 切换完成状态
    toggleState(state) {
      this.$emit('toggleState',state)
    },
    clearAllDone(){
      this.$emit('clearAllDone')
    }
  },
};
</script>

<style>
</style>
