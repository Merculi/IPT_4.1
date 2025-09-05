<script setup lang="ts">
import { computed } from 'vue'
import { ref } from 'vue'
import { onMounted } from 'vue'

const tasks = ref([
  { text: 'Rasen mähen',        done: false, high_priority: false, predictedHours: 2 },
  { text: 'Französisch lernen', done: false, high_priority: true, predictedHours: 1 },
  { text: 'Einkaufen',          done: false, high_priority: false, predictedHours: 5 },
  { text: 'Abfall rausbringen', done: false, high_priority: true, predictedHours: 4 },
])

onMounted(() => {
  tasks.value.sort((a, b) => b.high_priority - a.high_priority)
})

let sortedList = computed(() => {
  return tasks.value.sort((a,b) => b.high_priority - a.high_priority)
})

let newTaskText = ref("")
let newTaskPrio = ref(false)
let predictedHour = ref(0)
function AddTask(){
  if(newTaskText.value === "") return
  tasks.value.push({text: newTaskText.value, done: false, high_priority: newTaskPrio.value, predictedHours: predictedHour} )
  newTaskText.value = ""
  predictedHour = 0
  newTaskPrio.value = false
}

let finTasks = computed(() => tasks.value.filter(task => task.done).length)

function DeleteTask(text){
  tasks.value = tasks.value.filter(task => task.text !== text)
}

function CountOpenTasks(){
  let count = 0
  tasks.value.filter(task => !task.done ? count+=task.predictedHours : "")
  return count
}
</script>

<template>
  <div class="container">
    <h2>
      Aufgabenliste
    </h2>

    <p>
      {{finTasks}} von {{tasks.length}} Tasks sind erledigt, {{CountOpenTasks()}} h Aufwand offen
    </p>

    <div class="form-group">
      <label for="task">Neuer Task</label>
      <input v-model="newTaskText" class="form-control" id="task" type="text" placeholder="Rasen mähen ...">
    </div>

    <label for="prio">
      <input v-model="newTaskPrio" id="prio" type="checkbox">
      Hohe Priorität
    </label>


    <label for="predHour">
      <input v-model="predictedHour" id="predHour" type="number">
      Geschätzte Stunden
    </label>

    <div class="form-actions">
      <button @click="AddTask">
        Task hinzufügen
      </button>
    </div>

    <ul>
      <li v-for="task in sortedList" :class="{ 'high-priority': task.high_priority, 'is-done': task.done }">
        ca. {{task.predictedHours}}h {{task.text}}
        <input type="checkbox" v-model="task.high_priority"/>
        <button @click="DeleteTask(task.text)">Löschen</button>
      </li>
    </ul>
    <div>
    </div>

  </div>
</template>

<style>
.is-done {
  text-decoration: line-through;
}

.high-priority {
  font-weight: bold;
  color: red;
}

.form-group {
  display: block;
}

.form-group label {
  display: block;
  margin-bottom: 2px;
}

.form-control {
  width: 100%;
  padding: 2px 5px;
  height: 32px;
  margin-bottom: 5px;
}

.form-actions {
  display: block;
  margin-top: 1rem;
  margin-bottom: 2rem;
}

.container {
  margin: 20px auto;
  max-width: 400px;
  width: 100%;
}
</style>