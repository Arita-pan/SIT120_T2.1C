<script setup>
import { ref } from 'vue'

const todoId = ref(0)
const todolist = ref([])
const todoitem = ref('')
const complete = ref(false)

function add() {
  todolist.value.push({
    id: todoId.value++,
    item: todoitem.value,
    status: complete.value
  })
  todoitem.value = ""
}

function remove(todo) {
  todolist.value = todolist.value.filter((t) => t !== todo)
}

</script>

<template>
  <div>
    <h1>To Do List</h1>
    <form>
      <input type="text" placeholder="e.g. Grocery" v-model="todoitem">
      <button class="buttonstyle" @click="add" type="button" value="Add">Add</button>
    </form>
    <ol>
      <li v-for="i in todolist" :key="i.id">
      <input type="checkbox" v-model ="i.complete" class="crossout" value="checkbox">
      <span :class="{done: i.complete}">{{ i.item }}</span>
      <button @click="remove(i)" type="button" class="remove">x</button>
        
      </li>
    </ol>
  </div>
</template>

<style scoped>

h1{
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  text-align: center;
  margin-bottom: 20px;
}

button:hover {
  background-color: pink;
}

header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
