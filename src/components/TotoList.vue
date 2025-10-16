<script setup lang="ts">
import { ref } from 'vue'

interface Item {
    name: string
    completion : boolean
}

const TodoList = ref<Item[]>([

])

const newTaskName = ref('')
const newTaskCompletion = ref(false)

const addTask = () => {
    if (newTaskName.value != ('')) {
        TodoList.value.push({ name: newTaskName.value, completion: newTaskCompletion.value })
        newTaskName.value = ('')
        newTaskCompletion.value = (false)
    }
}
const Complete = (task:Item) =>{
  task.completion = true
}


</script>

<template>
  <div>
    <div>TodoList</div>
    <ul>
      <div>Completed Task List</div>
      <div v-for = "task in TodoList" :key="task.name">
        <li v-if="task.completion == true">
          <div>{{ task.name }}</div>
        </li>
      </div>

      <div>Uncompleted Task List</div>
      <div v-for = "task in TodoList" :key="task.name">
        <li v-if="task.completion == false">
            <div>{{ task.name }}</div>
            <button @click="Complete(task)">完了</button>
        </li>
      </div>
    </ul>
    <div>
      <label>
        タスク
        <input v-model="newTaskName" type="text" />
      </label>
      <label>
        完了
        <input v-model="newTaskCompletion" type="checkbox" />
      </label>
      <button @click="addTask">追加</button>
    </div>
  </div>
</template>

<style>

</style>