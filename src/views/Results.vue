<template>
  <div id="app">
    <v-list flat class="pt-0">
      <v-list-item-group multiple active-class="">
        <div v-for="(entry, index) in entries.slice().reverse()" :key="index">
          <v-list-item>
            <template v-slot:default="{ active }">

               <v-list-item-action>
                <v-checkbox :input-value="active"></v-checkbox>
              </v-list-item-action>

              <v-list-item-content>
                <v-list-item-title
                  ><EntryNote :entry="entry"></EntryNote
                ></v-list-item-title>
                <v-list-item-subtitle
                  ><span class="pl-7">{{
                    entry.result ? "Negative" : "Positive"
                  }}</span></v-list-item-subtitle
                >
              </v-list-item-content>

              <v-list-item-action>
                <v-btn @click.stop="deleteEntry(index)" icon>
                  <v-icon color="primary lighten-1">mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
              
            </template>
          </v-list-item>
          <v-divider></v-divider>
        </div>
      </v-list-item-group>
    </v-list>

    <Print></Print>

    <addEntry v-on:add-entry-event="addEntry" :entries="entries"></addEntry>
  </div>
</template>

<script>
import EntryNote from "../components/EntryNote.vue";
import AddEntry from "../components/AddEntry.vue";
import Print from "../components/Print.vue";
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
    },
    deleteEntry(id) {
      console.log(id);
    },
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
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
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
