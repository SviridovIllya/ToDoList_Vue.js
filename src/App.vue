<template>
  <div id="app">
    <h1 class="title">{{title}}</h1>
    <div class="todo">
      <input v-model="todo" type="text" placeholder="type todo..."/>
      <button @click="addTodo(id++)">add todo</button>
      <div v-for="(todo, i) in todos" :key="todo.id">
        <p>
          <span class="todo__id"> {{i+1}}.</span>
          <span class="todo__text"
                :class="{todo__isshow: todo.isComplete}"
                @dblclick="removeTodo(i)"
          >
            {{todo.text}}
          </span>

          <input v-model="todo.isComplete" class="todo__check" type="checkbox"/>
        </p>
      </div>
      <hr>
      <p>Task: {{todos.length}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      title: "Todo app",
      todo: " ",
      todos: [],
      isDone: false,
      id: 0,
    };
  },
  methods: {
    addTodo(){
      if (this.todo !=""){
        this.todos.push({
          id:this.id,
          text:this.todo,
          isComplete: this.isDone,
      });
      }
      this.todo="";
    },
    removeTodo(index){
      console.log(index);
      this.todos.splice(index,1);
    }
  }
};
</script>

<style>
#app {
}
.title{
  text-align: center;
}
.todo{
  width: 300px;
  height: 100%;
  background: #fff2f2;
  padding: 30px;
  outline: 1px solid #000;
  min-height: 500px;
}
.todo__id{
  color: red;
  font-weight: bold ;
}
.todo__text{
  font-size: 15px;
  color: #444;
  text-transform: capitalize;
}
.todo__isshow{
  color: #ccc;
  text-decoration: line-through;
}
.todo__check{
  display: inline-block;
  margin-left: 10px;
}
</style>
