<template>
  <section class="main">
    <input id="toggle-all" class="toggle-all" type="checkbox">
    <label for="toggle-all">Mark all as complete</label>
    <ul class="todo-list">
      <!-- These are here just to show the structure of the list items -->
      <!-- List items should get the class `editing` when editing
      and `completed` when marked as completed-->
      <li class = "editing" v-for="(item) in todo" :key="item.id" :class="item.completed ? 'completed' : '' ">
        <div class="view">
          <input class="toggle" type="checkbox" v-model="item.completed">
          <label>{{item.content}}</label>
          <button class="destroy" @click="del(item.id)"></button>
        </div>
        <input class="edit">
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    todo: {
      type: Array,
      required: true
    }
  },
  methods: {
    del(id) {
      this.$emit('del',id)
    }
    // delTodo() {
    //   this.$emit('del', this.todo.id);
    // }
  }
}
</script>

<style>
</style>
