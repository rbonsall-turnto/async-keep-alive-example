<template>
  <h1>Hello World Async - Keep Alive</h1>

  <p>
    Component is loaded async.  State should be kept alive, but is not.
  </p>

  <button @click="state.count++">count is: {{ state.count }}</button>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'hello-world-async',
  setup() {
    const state = reactive({ count: 0 })

    return {
      state
    }
  }
}
</script>
