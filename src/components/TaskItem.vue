<template>
    <li>
      <div class="list_item">
        <input type="checkbox" v-model="task.done" @change="$emit('toggle-done')" />
        <i :class="{ expired: isExpired && !task.done }">{{ task.date }}</i>
        <span :class="{ cheked: task.done }">{{ task.name }}</span>
      </div>
      <div class="list-btn">
        <button @click="$emit('edit', index)">
          <img src="./images/icon-pencil.png" alt="edit" />
        </button>
        <button
          @click="$emit('delete', index)"
          :disabled="isEditing"
          :class="{ disabledBtn: isEditing }"
        >
          <img src="./images/delete-icon.png" alt="delete" />
        </button>
      </div>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      task: Object,
      index: Number,
      isEditing: Boolean,
    },
    computed: {
      isExpired() {
        const today = new Date().toISOString().split('T')[0];
        return this.task.date < today;
      }
    }
  };
  </script>
  