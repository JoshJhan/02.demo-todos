<template>
  <div class="input-container">
    <form class="form-inline" @submit.prevent="onFormSubmit">
      <div class="input-group mb-2 mr-sm-2">
        <div class="input-group-prepend">
          <div class="input-group-text">任務</div>
        </div>
        <input
          type="text"
          class="form-control"
          placeholder="請輸入任務訊息"
          style="width: 256px"
          v-model.trim="taskname"
        />
      </div>

      <button type="submit" class="btn btn-primary mb-2">添加新任務</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "TodoInput",
  emits: ["add"],
  data() {
    return {
      // 新任務名稱
      taskname: "",
    };
  },
  methods: {
    // 表單提交的事件處理函數
    onFormSubmit() {
      // 1. 判斷任務名稱是否為空
      if (!this.taskname) return alert("任務名稱不能為空! ");

      //2.觸發定義的add事件並向外界傳遞數據
      this.$emit("add", this.taskname);
      //3.清空輸入框
      this.taskname = "";
    },
  },
};
</script>

<style lang="less" scoped>
.input-container {
    border:3px solid hotpink;
}
</style>
