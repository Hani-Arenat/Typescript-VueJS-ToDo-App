<template>
  <div>
    <h3>TypeScript VueJS ToDo APP</h3>
    <div class="addTodo">
      <input type="text" v-model="todoText" />
      <button @click="addTodo">Add Task</button>
    </div>
    <div class="todoList">
      <p v-for="(todo, index) in todoList" class="todoItem" :key="index">
        <span>{{ todo }}</span>
        <span @click="removeTask(index)" class="remove">remove</span>
      </p>
    </div>
    <div v-if="todoList.length > 0" class="select-section">
      <button class="remove-all" @click="removeAll">remove all Tasks</button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class TodoList extends Vue {
  todoText = "";
  todoList: string[] = [];
  addTodo(): void {
    if (this.todoText.length === 0) {
      return;
    }
    this.todoList.push(this.todoText);
    this.todoText = "";
  }
  removeAll(): void {
    this.todoList = [];
    this.todoText = "";
  }
  removeTask(index: number): void {
    this.todoList.splice(index, 1);
    this.todoText = "";
  }
}
</script>

<style>
.remove-all {
  width: 70%;
  margin: 20px auto;
}
.remove {
  float: right;
  color: red;
  cursor: pointer;
}
input {
  width: 200px;
  height: 35px;
  border-radius: 2px;
  border: 1px solid #a5a5a5;
  margin-top: 10px;
  padding-left: 5px;
}
button {
  width: 90px;
  height: 37px;
  background-color: #42b983;
  color: white;
  border-radius: 2px;
  border: 1px solid #42b983;
  cursor: pointer;
}
.addTodo {
  width: 310px;
  height: 40px;
  margin: 0 auto;
}
.todoList {
  width: 290px;
  min-height: 140px;
  margin: 40px auto;
  padding-left: 5px;
  padding-top: 5px;
  margin-top: 20px;
  margin-bottom: 50px;
}
.todoItem {
  width: 95%;
  height: 20px;
  text-align: left;
  border-bottom: 1px solid #b8b8bf;
  padding-bottom: 5px;
}
.todoItem:hover {
  color: black;
}
.select-section {
  width: 300px;
  height: 40px;
  margin: 0 auto;
  margin-top: -40px;
}
</style>
