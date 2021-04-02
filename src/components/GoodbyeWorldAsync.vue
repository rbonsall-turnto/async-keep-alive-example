<template>
  <h1>Goodbye World Async - Do Not Keep Alive</h1>

  <p>
    Loaded async, not included in keep-alive, so state should not be maintain.
  </p>

  <button @click="state.count++">count is: {{ state.count }}</button>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'goodbye-world-async',
  setup() {
    const state = reactive({ count: 0 })

    return {
      state
    }
  }
}
</script>
