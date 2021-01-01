<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <div v-for="(accion, index) in listActions" :key="index">
      <span>
        {{accion.action}}(
          <span v-for="(params, id) in accion.parameters" :key="id">
            {{params}},
          </span>
        )
        
      </span>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <VueFlow @newAction="eventNewAction"/>
  </div>
</template>

<script>
import VueFlow from './components/dialogFlow.vue'

export default {
  name: 'App',
  data: () => ({
    listActions: []
  }),
  components: {
    VueFlow
  },
  methods: {
    eventNewAction(newAction){
      this.listActions.push(newAction)
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
</style>
