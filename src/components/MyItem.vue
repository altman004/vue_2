<template>
  <li>
    <label>
      <input
        type="checkbox"
        :checked="todo.done"
        @click="handleCheck(todo.id)"
      />
      <!-- 修改props违背原则，不推荐，Vue2会报错 -->
      <!-- <input type="checkbox" v-model="todo.done" /> -->
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" @click="handleDeleteBtn(todo.id)">
      删除
    </button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  props: ["todo", "checkTodo", "deleteItem"],
  methods: {
    handleCheck(id) {
      // 通知App组件将对应的todo对象done取反
      this.checkTodo(id);
    },
    handleDeleteBtn(id) {
      if (confirm("确定删除吗？")) {
        this.deleteItem(id);
      }
    },
  },
};
</script>

<style scoped>
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}
li label {
  float: left;
  cursor: pointer;
}
li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}
li button {
  float: right;
  display: none;
  margin-top: 3px;
}
li:before {
  content: initial;
}
li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: #ddd;
}
li:hover button {
  display: block;
}
</style>