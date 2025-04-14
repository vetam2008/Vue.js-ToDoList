<template>
    <div class="todo_header">
      <input type="search" :value="search" @input="$emit('update:search', $event.target.value)" placeholder="Пошук" />
      <select :value="filterStatus" @change="$emit('update:filterStatus', $event.target.value)" class="todo_filter">
        <option value="all">Усі</option>
        <option value="done">Виконані</option>
        <option value="inProgress">В процесі</option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    props: ['search', 'filterStatus']
  };
  </script>
  