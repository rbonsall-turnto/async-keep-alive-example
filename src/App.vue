<template>
  <div class="tab">
    <button class="tablink" :class="{'active': component === 'hello-world'}" @click="showHello">Hello World</button>
    <button class="tablink" :class="{'active': component === 'hello-world-async'}" @click="showHelloAsync">Hello World Async</button>
    <button class="tablink" :class="{'active': component === 'goodby-world-async'}" @click="showGoodbyeAsync">Goodbye World Async</button>
  </div>
  <div class="tabcontent">
    <keep-alive :include="['hello-world', 'hello-world-async']">
      <component :is="component"></component>
    </keep-alive>
  </div>
</template>

<script>
import { defineAsyncComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  data () {
    return {
      component: 'hello-world'
    }
  },
  components: {
    'hello-world': HelloWorld,
    'hello-world-async': defineAsyncComponent(
      () => import('./components/HelloWorldAsync.vue')
    ),
    'goodbye-world-async': defineAsyncComponent(
      () => import('./components/GoodbyeWorld.vue')
    )
  },
  methods: {
    showHello() {
      this.component = 'hello-world'
    },
    showHelloAsync() {
      this.component = 'hello-world-async'
    },
    showGoodbyeAsync() {
      this.component = 'goodbye-world-async'
    }
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  /* client tab styles */
  .tab {
    max-width: 1000px;
    overflow: hidden;
    border: 1px solid #ccc;
    background-color: #f1f1f1;
  }

  .tablink {
    background-color: inherit;
    float: left;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 14px 16px;
    transition: 0.3s;
  }

  .tab button:hover {
    background-color: #ddd;
  }

  .tab button.active {
    background-color: #ccc;
  }

  .tabcontent {
    max-width: 1000px;
    padding: 6px 12px;
    border: 1px solid #ccc;
    border-top: none;
  }
</style>