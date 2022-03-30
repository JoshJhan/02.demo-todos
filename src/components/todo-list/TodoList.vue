<template>
  <ul class="list-group">
    <!-- 列表組 -->
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in list" :key="item.id">
        <!-- 複選框 -->
        <div class="form-check">
            <input class="form-check-input" type="checkbox" value="" :id="item.id" v-model="item.done">
            <label class="form-check-label" :class="item.done ? 'delete' : ''" :for="item.id">
                {{item.task}}
            </label>
        </div>
        <!-- 徽標 -->
        <span class="badge bg-success rounded-pill" v-if="item.done">完成</span>
        <span class="badge bg-warning rounded-pill" v-else>未完成</span>
    </li>
</ul>
</template>

<script>
export default {
    name:'TodoList',
    props:{
        //列表數據
        list:{
            type:Array,
            required:true,
            default:[],
        }
    }
}
</script>

<style lang="less" scoped>
    .list-group {
        border: 3px solid chartreuse;
        width: 400px;
    }
    .delete {
        text-decoration: line-through;
        color:gray;
        font-style: italic;
    }
</style>