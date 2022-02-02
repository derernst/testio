<template>
  <div id="app" style="padding: 20px">
    <h1>Testio</h1>
    <Print></Print>
    <div v-for="(entry, index) in entries.slice().reverse()" :key="index">
      <EntryNote :entry="entry"></EntryNote>
    </div>
    <addEntry v-on:add-entry-event="addEntry" :entries="entries"></addEntry>
  </div>
</template>

<script>
import EntryNote from "./components/EntryNote.vue";
import AddEntry from "./components/AddEntry.vue";
import Print from "./components/Print.vue";

export default {
  name: "App",
  components: {
    // HelloWorld
    EntryNote,
    AddEntry,
    Print,
  },
  data() {
    return {
      entries: [],
    };
  },
  methods: {
    addEntry(newEntry) {
      this.entries = [...this.entries, newEntry];
    }
  },
  mounted() {
    if (localStorage.getItem("entries")) {
      this.entries = JSON.parse(localStorage.getItem("entries"));
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

ul {
  padding-left: 0;
}

li {
  list-style-type: none;
}
.print-button {
  position: absolute;
  top: 20px;
  right: 20px;
}
</style>
