<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <Form @onSaveTask="saveTask" />

      <div class="lista">
        <Task v-for="(task, index) in tasks" :key="index" :task="task" />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Form from './components/Form.vue'
import SideBar from './components/SideBar.vue'
import Task from './components/Task.vue'

import ITask from './interfaces/ITask'

export default defineComponent({
  name: 'App',
  components: { Form, SideBar, Task },
  data () {
    return {
      tasks: [] as ITask[]
    }
  },
  methods: {
    saveTask (task: ITask) {
      this.tasks.push(task)
    }
  }
});
</script>

<style>
  .lista {
    padding: 1.25rem;
  }
</style>
