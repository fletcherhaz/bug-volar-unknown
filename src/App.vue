<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" :test="test" v-slot="{ state, updateState }">
    <button @click="updateState">COUNT IS: {{ state.count }}</button>
  </HelloWorld>
</template>

<script lang="ts">
export type Generic<T> = {
  state: T,
  updateState: () => void
}
</script>

<script lang="ts" setup>
import { reactive } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

const test: Generic<{ count: 0 }> = {
  state: reactive({
    count: 0
  }),
  updateState: () => {
    test.state.count += 1
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
</style>