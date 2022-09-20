<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          v-model="task"
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja inciar?"
        />
      </div>

      <div class="column">
        <TimerSection @onTimerFinished="taskFinished" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  import TimerSection from './TimerSection.vue'

  export default defineComponent({
    name: 'FormTracker',
    emits: ['onSaveTask'],
    components: { TimerSection },
    data () {
      return {
        task: ''
      }
    },
    methods: {
      taskFinished (elapsedTime: number): void {
        this.$emit('onSaveTask', {
          description: this.task,
          duration: elapsedTime
        })
        this.task = ''
      },
    }
  })
</script>

<style>
  .form {
    background-color: var(--bg-primary);
    color: var(--text-primary);
  }
</style>