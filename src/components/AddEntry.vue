<template>

  <b-button-toolbar style="position: fixed; bottom: 20px; right: 20px" key-nav>

      
    <b-button-group class="mx-1">
      <b-button variant="success" @click="addEntryNote(true)">
        <b-icon icon="check-circle-fill"></b-icon> <span>Negative</span>
      </b-button>
      <b-button variant="danger" @click="addEntryNote(false)">
        <b-icon icon="x-circle-fill"></b-icon> <span>Positive</span>
      </b-button>
    </b-button-group>
  </b-button-toolbar>
</template>

<script>
export default {
  name: "AddEntry",
  props: {
    entries: Array,
  },
  methods: {
    addEntryNote(resultInput) {
      var today = new Date();
      const newEntry = {
        date: today.toLocaleString("de-DE"),
        result: resultInput,
      };
      this.$emit("add-entry-event", newEntry);
    },
  },
  watch: {
    entries: {
      handler() {
        localStorage.setItem("entries", JSON.stringify(this.entries));
      },
      deep: true,
    },
  }
};
</script>

<style scoped></style>
