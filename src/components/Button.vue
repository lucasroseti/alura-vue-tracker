<template>
  <button class="button" @click="onButtonClick" :disabled="isDisabled">
    <span class="icon">
      <i :class="`fas ${icon}`"></i>
    </span>
    <span>{{label}}</span>
  </button>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'ButtonTracker',
    emits: ['onButtonClick'],
    props: {
      isDisabled: { type: Boolean, default: false },
      icon: { type: String, default: 'fa-stop' },
      label: { type: String, default: 'stop' }
    },
    methods: {
      onButtonClick (): void {
        this.$emit('onButtonClick')
      }
    }
  })
</script>