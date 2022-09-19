<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Timer :timeInSeconds="timeInSeconds" />
    <Button icon="fa-play" label="play" :isDisabled="timerIsRunning" @onButtonClick="start" />
    <Button :isDisabled="!timerIsRunning" @onButtonClick="stop" />
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'

  import Button from './Button.vue'
  import Timer from './Timer.vue'

  export default defineComponent({
    name: 'TimerSectionTracker',
    emits: ['onTimerFinished'],
    components: { Button, Timer },
    data () {
      return {
        timeInSeconds: 0,
        timer: 0,
        timerIsRunning: false
      }
    },
    methods: {
      start () {
        this.handleTimerRunning()
        this.timer = setInterval(() => {
          this.timeInSeconds += 1
        }, 1000)
      },
      stop () {
        this.handleTimerRunning()
        clearInterval(this.timer)
        this.$emit('onTimerFinished', this.timeInSeconds)
        this.timeInSeconds = 0
      },
      handleTimerRunning() {
        this.timerIsRunning = !this.timerIsRunning
      }
    }
  })
</script>