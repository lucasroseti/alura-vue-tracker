<template>
  <main class="columns is-gapless is-multiline" :class="{'dark-mode': darkMode}">
    <div class="column is-one-quarter">
      <SideBar @onChangeTheme="changeTheme"/>
    </div>
    <div class="column is-three-quarter content">
      <Form @onSaveTask="saveTask" />

      <div class="lista">
        <Task v-for="(task, index) in tasks" :key="index" :task="task" />
        <Box v-if="listIsEmpty">Você não está muito produtivo hoje!</Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Box from './components/Box.vue'
import Form from './components/Form.vue'
import SideBar from './components/SideBar.vue'
import Task from './components/Task.vue'

import ITask from './interfaces/ITask'

export default defineComponent({
  name: 'App',
  components: { Box, Form, SideBar, Task },
  data () {
    return {
      tasks: [] as ITask[],
      darkMode: false
    }
  },
  computed: {
    listIsEmpty () : boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    changeTheme (isDarkMode: boolean) {
      console.log(isDarkMode)
      this.darkMode = isDarkMode
    },
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
  main {
    --bg-primary: #fff;
    --text-primary: #000;
  }
  main.dark-mode {
    --bg-primary: #2b2d42;
    --text-primary: #ddd;
  }
  .content {
    background-color: var(--bg-primary);
  }
</style>
