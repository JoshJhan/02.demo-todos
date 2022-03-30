<template>
  <div class="root-container">
    <h1>App 根組件</h1>
    <hr />

    <!-- 使用 TodoInput 子組件-->
    <TodoInput @add="onAddNewTask" />
    <!-- 使用 TodoList 子組件-->
    <TodoList :list="taskList" class="mt-2" />
    <!-- 使用 TodoButton 子組件-->
    <TodoButton v-model:active="activeBtnIndex" />
  </div>
</template>

<script>
// 步驟1 : 引入各組件
import TodoList from "./components/todo-list/TodoList.vue";
import TodoInput from "./components/todo-input/TodoInput.vue";
import TodoButton from "./components/toso-button/TodoButton.vue";

export default {
  name: "MyApp",
  // 步驟2.宣告 components
  components: {
    TodoList,
    TodoInput,
    TodoButton,
  },
  data() {
    return {
      // 任務列表的數據
      todolist: [
        { id: 1, task: "周一早晨9點開會", done: false },
        { id: 2, task: "周一晚上8點聚餐", done: false },
        { id: 3, task: "準備週三晚上的演講", done: true },
      ],
      nextId: 4, // 下一個可用ID
      activeBtnIndex: 0, // tab: 0(全部);1(已完成);2(未完成)
    };
  },
  methods: {
    //-- 方法：新增任務
    onAddNewTask(taskname) {
      this.todolist.push({
        id: this.nextId,  
        task: taskname,
        done: false,
      });
      this.nextId++;
    },
  },
  computed: {
    taskList() {
      switch (this.activeBtnIndex) {
        case 0:
          return this.todolist;
        case 1:
          return this.todolist.filter((x) => x.done === true);
        case 2:
          return this.todolist.filter((x) => x.done !== true);
      }
    },
  },
};
</script>

<style lang="less" scoped>
.root-container{
  border: 3px solid yellow;
}
</style>
