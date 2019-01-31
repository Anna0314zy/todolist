<template>
  <div>
    <input class="new-todo" placeholder="What needs to be done?" @keyup.enter="addTodo">
    <Items 
    :todo="filterTodo"
    @del="delTodo"
    ></Items>
    <Tabs
    :todo="filterTodo"
    :filter="filter"
    @toggleState="toggleState"
    @clearAllDone="clearAllDone"
    ></Tabs>
  </div>
  <!-- This footer should hidden by default and shown when there are todos -->
</template>

<script>
import Tabs from "./tabs"
import Items from "./items"
let id = 0
export default {
  components: {
    Tabs,
    Items
  },
 data() {
   return {
     todos:[],
     confirmed:false,
     filter:'all'
   }
 },
 computed: {
    filterTodo() {
      if(this.filter === 'all') {
        return this.todos
      }
      // 当filter是completed completed 为真
      // 当filter是active completed 为假
      const completed = this.filter === 'completed'
      return this.todos.filter(todo=>completed === todo.completed)
    }
 },
  methods: {
    removeTodo() {},
    addTodo(e) {
      console.log(e.target.value)
      this.todos.unshift({
        id:id++,
        content:e.target.value,
        completed:false
      })
     e.target.value=""
    },
   
    delTodo(id){
      // console.log(id)
      this.todos.splice(this.todos.findIndex((todo)=>todo.id === id),1)
    },
    toggleState(state) {
      this.filter = state
    },
    clearAllDone() {
      // 留下completed是false的
     this.todos = this.todos.filter(todo=>!todo.completed)
    }
  }
};
</script>

<style>
</style>
