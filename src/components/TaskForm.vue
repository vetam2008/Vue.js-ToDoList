<template>
    <div class="todo_head">
      <input 
        type="date" 
        :min="minDate" 
        :value="taskDate" 
        @input="$emit('update:taskDate', $event.target.value)"
      />
      <input
        type="text"
        :value="task"
        placeholder="Додайте завдання"
        @input="$emit('update:task', $event.target.value)"
        @keypress.enter="$emit('submit-task')"
      />
      <button class="todo_add_btn" @click="$emit('submit-task')">Додати</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['task', 'taskDate'],
    computed: {
      minDate() {
        return new Date().toISOString().split('T')[0];
      }
    }
  };
  </script>
  