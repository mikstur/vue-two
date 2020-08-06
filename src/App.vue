<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div v-bind:id="messageId">{{ message }}</div>
    <div>{{ appendSomething }} - {{ sum(1, 2) }}</div>

    <div> {{orderedOn}} </div>

    <div> {{prettyOrderedOn}} </div>

    <div v-for="item of items" :key="item.id">
      {{item.title}}
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data: () => {
    return {
      messageId: "message-id123",
      message: "Test Message test",
      orderedOn: new Date(),
      items: [
        {
          id: 1,
          title: "Hello"
        },
        {
          id: 2,
          title: "Hello"
        },
        {
          id: 3,
          title: "Hello"
        }
      ]
    }
  },
  created: function () {
    console.log("Lets fetch some data from Firebase...");
    this.fetchItems();
  },
  computed: {
    appendSomething: function () {
      return this.message + " something";
    },
    prettyOrderedOn: function() {
      return this.orderedOn.getMonth() + " - " + this.orderedOn.getFullYear()
    }
  },
  methods: {
    sum: function(a, b) {
      return a + b;
    },
    fetchItems: function() {
      // Go to firebase 
      this.items = [
        {
          id: 1,
          title: "Hello"
        }
      ]
    }
  },
  components: {
    HelloWorld,
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
