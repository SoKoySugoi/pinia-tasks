<template>
  <main>

    <!-- header -->
    <header>
      <img src="./assets/pnia-logo.svg" alt="pinia logo">
      <h1>{{ taskStore.name }}</h1>
    </header>

    <!-- new task form -->
     <div class="new-task-form">
      <task-form />
     </div>

    <!-- filter -->
    <nav class="filter">
      <button @click="filter = 'all'">All tasks</button>
      <button @click="filter = 'favs'">Favorite tasks</button>
          <!-- reset state -->
      <button class="reset" @click="taskStore.$reset">Reset state</button>
    </nav>

    <!-- loading -->
    <div class="loading" v-if="isLoading">Loading tasks...</div>
    <div v-else>
      <!-- task list -->
      <div class="task-list" v-if="filter === 'all'">
        <p>You have {{ totalCount }} total tasks</p>
          <div v-for="task in tasks">
            <task-details :task="task"/>
          </div>
      </div>
      <div class="task-list" v-if="filter === 'favs'">
        <p>{{ favCount }} favorite tasks</p>
        <div v-for="task in favs">
            <task-details :task="task"/>
        </div>
      </div>
    </div>

  </main>
</template>

<script>
  import { ref } from 'vue'
  import TaskDetails from './components/TaskDetails.vue'
  import TaskForm from './components/TaskForm.vue'
  import { useTaskStore } from '@/stores/TaskStore'
  import { storeToRefs } from 'pinia'
  
  export default {
    components: { TaskDetails, TaskForm },
    setup () {
      const taskStore = useTaskStore()

      const { tasks, isLoading, favs, totalCount, favCount } = storeToRefs(taskStore)

      // fetch tasks
      taskStore.getTasks()

      const filter = ref('all')

      return { taskStore, filter, tasks, isLoading, favs, totalCount, favCount}
    }
  }
</script>
