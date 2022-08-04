<template>
  <h1>根组件</h1>
  <hr />
  <TodoInput @add="onAddNewTask"></TodoInput>
  <TodoList :list="tasklist" class="mt-2"></TodoList>
  <TodoButton v-model:active="activeBtnIndex"></TodoButton>
</template>

<script>
import TodoList from './components/todo-list/TodoList.vue'
import TodoInput from './components/todo-input/TodoInput.vue'
import TodoButton from './components/todo-button/TodoButton.vue'
export default {
  name: 'MyApp',
  components: {
    TodoList,
    TodoInput,
    TodoButton
  },
  data() {
    return {
      // 任务列表的数据
      todolist: [
        { id: 1, task: '周一早晨9点开会', done: false },
        { id: 2, task: '周一晚上8点聚餐', done: false },
        { id: 3, task: '准备周三上午的演讲稿', done: true }
      ],
      nextId: 4,
      activeBtnIndex: 0
    }
  },
  methods: {
    onAddNewTask(taskname) {
      console.log(taskname)
      this.todolist.push({
        id: this.nextId,
        task: taskname,
        done: false
      })
      // 一定要加this，不能省略，否则报错。
      this.nextId++
    }
  },
  computed: {
    tasklist() {
      switch (this.activeBtnIndex) {
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter((x) => x.done)
        case 2:
          return this.todolist.filter((x) => !x.done)
      }
    }
  }
}
</script>

<style lang="less" scoped></style>
