<template>
  <Box>
    <div class="columns">
      <div class="column is-7">{{task.description || 'Tarefa sem descrição'}}</div>
      <div class="column">
        <Timer :timeInSeconds="task.duration" />
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
  import { defineComponent, PropType } from 'vue'
  import Box from './Box.vue'
  import Timer from './Timer.vue'
  import ITask from '../interfaces/ITask'

  export default defineComponent({
    name: 'TaskTracker',
    components: { Box, Timer },
    props: {
      task: { type: Object as PropType<ITask>, required: true }
    }
  })
</script>

<style scoped>
  .box {
    background: #FAF0CA;
  }
</style>