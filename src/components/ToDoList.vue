<template>
  <div>
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
  </div>
</template>

<script>
export default {
  props:{
    todos:{
      type: [Object, Array],
      required: true
    }
  }
}
</script>