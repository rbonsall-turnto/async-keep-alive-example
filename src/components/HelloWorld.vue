<template>
  <h1>Hello World - Keep alive</h1>

  <p>
    Component is not loaded async.  State is kept alive.
  </p>

  <button @click="state.count++">count is: {{ state.count }}</button>
</template>

<script>
import { reactive } from 'vue'

export default {
  name: 'hello-world',
  setup() {
    const state = reactive({ count: 0 })

    return {
      state
    }
  }
}
</script>
