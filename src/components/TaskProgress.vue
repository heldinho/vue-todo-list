<template>
  <div class="tasks-progress">
    <span class="progress-value">{{ progress }}%</span>
    <div class="progress-bar" :style="{ width: progress + '%' }"></div>
  </div>
</template>

<script>
export default {
  name: 'TaskProgress',
  props: {
    progress: {
      type: Number,
      default: 0
    }
  },
  data: () => ({})
}
</script>

<style scoped>
.tasks-progress {
  position: relative;
  width: 80%;
  height: 30px;
  border: 1px solid #fff;
  color: #fff;
  border-radius: 8px;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
  overflow: hidden;
}

.progress-bar {
  position: absolute;
  height: 100%;
  background-color: #4caf50;
  align-self: flex-start;
}

.progress-value {
  z-index: 1;
  font-size: 1.5rem;
}
</style>
