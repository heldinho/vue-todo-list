<template>
  <div
    @click="$emit('taskStateChanged', task)"
    class="task"
    :class="stateClass"
  >
    <span @click.self="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      }
    }
  }
}
</script>

<style scoped>
.task {
  position: relative;
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

.pending {
  border-left: 12px solid #b73229;
  background-color: #f44336;
}
.pending .close {
  background-color: #b73229;
}
.pending .close:hover {
  color: #444;
}

.done {
  color: #ddd;
  border-left: 12px solid #0a8f08;
  background-color: #4caf50;
  text-decoration: line-through;
}
.done .close {
  background-color: #0a8f08;
}
.done .close:hover {
  color: #444;
}

.close {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: 0.9rem;
  font-weight: 600;
  width: 30px;
  border-radius: 100px;
  display: flex;
  justify-content: center;
  line-height: 2;
}
</style>
