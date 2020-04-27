<template>
  <div class="task-grid">
    <template v-if="tasks.length">
      <Task
        v-for="(task, i) in tasks"
        :key="task.name"
        :task="task"
        @taskDeleted="$emit('taskDeleted', i)"
        @taskStateChanged="$emit('taskStateChanged', i)"
      ></Task>
    </template>
    <p class="no-task" v-else>Nenhuma tarefa atribuida.</p>
  </div>
</template>

<script>
import Task from './Task'
export default {
  name: 'TaskGrid',
  components: {
    Task
  },
  props: {
    tasks: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.task-grid {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.task-grid .task {
  margin: 10px;
}

.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
</style>
