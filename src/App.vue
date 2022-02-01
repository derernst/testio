<template>
  <div id="app" style="padding: 20px">
    <h1>Testio</h1>
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <ul>
      <li v-for="entry in entries" :key="entry.date"><EntryNote :testResult="entry.result"></EntryNote></li>
    </ul>
    <b-button-toolbar key-nav aria-label="Toolbar with button groups">
      <b-button-group class="mx-1">
        <b-button variant="success" @click="addEntryNote(true)">
          <b-icon icon="check-circle-fill"></b-icon>
        </b-button>
        <b-button variant="danger" @click="addEntryNote(false)">
          <b-icon icon="x-circle-fill"></b-icon>
        </b-button>
      </b-button-group>
    </b-button-toolbar>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import EntryNote from "./components/history/EntryNote.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    EntryNote,
  },
  data() {
    return {
      entries: []
    }
  },
  methods: {
    addEntryNote(resultInput) {
      var today = new Date();
      this.entries.push({
        date: today.getFullYear(),
        result: resultInput
      });
    }
  }
};
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
