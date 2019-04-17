<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <ol>
      <li v-for="[i, j] of lists.flat()" :key="`${i}-${j}`">
        {{ i + 1 }} - {{ String.fromCodePoint(j + 0x61) }}
      </li>
    </ol>

    <ol>
      <li v-for="item of flattened" :key="item" v-text="item" />
    </ol>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },

  data() {
    return {
      lists: Array.from({ length: 3 }, (_, i) =>
        Array.from({ length: 3 }, (_, j) => [i, j])
      )
    };
  },

  computed: {
    flattened() {
      return this.lists.flatMap(list =>
        list.map(([i, j]) => `${i + 1} - ${String.fromCodePoint(j + 0x61)}`)
      );
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
