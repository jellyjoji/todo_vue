<template>
  <div id="app" class="container">
    <div class="card card-body bg-light">
      <div class="title">Todolist App</div>
    </div>

    <div class="card card-default card-borderless">
      <div class="card-body">
        <InputTodo @add-todo="addTodo" />
        <TodoList :todoList="todoList" @delete-todo="deleteTodo" @toggle-completed="toggleCompleted" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoList from './components/Todolist.vue'
import InputTodo from './components/InputTodo.vue'

let ts = new Date().getTime()

export default {
  name:"App",
  components:{InputTodo,TodoList},
  data(){
    return{
      todoList:[
        {id:1, todo:'riding a cycling', completed:false},
        {id:2, todo:'running outside', completed:true},
        {id:3, todo:'riding a cycling', completed:false},
        {id:4, todo:'running outside', completed:true},
      ]
    }
  },
  methods:{
    addTodo(todo){
      if(todo.length >=2 ){
        this.todoList.push({id:new Date().getTime(), todo:todo, completed:false})
      }
    },
    deleteTodo(id){
      let index = this.todoList.findIndex((item)=>id===item.id);
      this.todoList.splice(index,1)
    },
    toggleCompleted(id){
      let index = this.todoList.findIndex((item)=>id===item.id);
      this.todoList[index].completed=!this.todoList[index].completed;
    }
  }

}
</script>

<style>

</style>