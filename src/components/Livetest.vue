<script setup>
import { ref } from 'vue';

const tasks = ref([
  { name: "Task 1", time: 30 },
  { name: "Task 2", time: 40 },
  { name: "Task 3", time: 60 },
  { name: "Task 4", time: 45 },
  { name: "Task 5", time: 50 }
]);

let showForm = ref(false)
let activeIndex = ref(0)
</script>

<template>
  <div class="container mx-auto">
    <h2>Task List - Live test (Ostad)</h2>
    <div class="p-4 bg-slate-100 rounded">
      <div class="my-3 p-2 bg-slate-200 flex justify-between items-center" v-for="(task, index) in tasks" :key="index">
        <div>
          <h2>Task Name: {{ task.name }}</h2>
          <p> - Time: {{ task.time }}</p>
        </div>
        <button @click="showForm = !showForm; activeIndex = index" class="px-3 py-1 bg-green-300 rounded">Edit
          Task</button>
      </div>
    </div>
    <div class="mx-4 p-2 bg-indigo-200 rounded" v-show="showForm">
      <input type="text" name="name" id="updateName" class="p-2 rounded border border-slate-200"
        v-model="tasks[activeIndex].name"><br>
      <input type="number" name="time" id="updateTime" class="my-2 p-2 rounded border border-slate-200"
        v-model="tasks[activeIndex].time"><br>
      <button class="px-3 py-1 bg-green-300 rounded" @click="showForm = false">Update Task/Close Popup</button>
    </div>
  </div>
</template>
<style></style>
