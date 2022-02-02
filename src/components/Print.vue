<template>
  <b-button class="print-button" @click="print()">
    <b-icon icon="printer"></b-icon>
  </b-button>
</template>

<script>
export default {
  name: "Print",
  methods: {
    print() {
      window.print();
    },
  },
};
</script>

<style scoped>

</style>
