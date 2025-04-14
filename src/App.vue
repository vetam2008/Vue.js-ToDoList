<template>
  <main class="app">
    <div class="todo_container">
      <div class="todo_fold">
        <TaskFilter 
          v-model:search="search" 
          v-model:filterStatus="filterStatus" 
        />

        <TaskForm 
          :task="task"
          :taskDate="taskDate"
          :editedTask="editedTask"
          @submit-task="submitTask"
          @update:task="task = $event"
          @update:taskDate="taskDate = $event"
        />

        <div class="todo_list">
          <ul>
            <p>Список справ: {{ filteredTasks.length }}</p>
            <TaskItem
              v-for="(task, index) in filteredTasks"
              :key="index"
              :task="task"
              :index="index"
              :isEditing="editedTask === index"
              @edit="editTask"
              @delete="deleteTask"
              @toggle-done="saveTasks"
            />
          </ul>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import TaskItem from './components/TaskItem.vue';
import TaskForm from './components/TaskForm.vue';
import TaskFilter from './components/TaskFilter.vue';

export default {
  components: { TaskItem, TaskForm, TaskFilter },

  data() {
    return {
      task: "",
      taskDate: "",
      editedTask: null,
      tasks: [],
      search: "",
      filterStatus: "all",
    };
  },

  computed: {
    filteredTasks() {
      let result = this.tasks;

      if (this.search.trim() !== "") {
        result = result.filter((task) =>
          task.name.toLowerCase().includes(this.search.toLowerCase())
        );
      }

      if (this.filterStatus === "done") {
        result = result.filter((task) => task.done);
      } else if (this.filterStatus === "inProgress") {
        result = result.filter((task) => !task.done);
      }

      return result;
    },
  },

  methods: {
    submitTask() {
      if (this.task.trim().length === 0) return;

      if (this.editedTask === null) {
        this.tasks.push({
          name: this.task,
          date: this.taskDate,
          done: false,
        });
      } else {
        this.tasks[this.editedTask].name = this.task;
        this.tasks[this.editedTask].date = this.taskDate;
        this.editedTask = null;
      }

      this.saveTasks();
      this.task = "";
      this.taskDate = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
      this.saveTasks();
    },

    editTask(index) {
      this.task = this.tasks[index].name;
      this.taskDate = this.tasks[index].date;
      this.editedTask = index;
    },

    saveTasks() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
  },

  mounted() {
    const saved = localStorage.getItem("tasks");
    if (saved) {
      this.tasks = JSON.parse(saved);
    }
  },
};
</script>

<style src="./components/assets/styles.css"></style>
