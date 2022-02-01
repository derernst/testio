<template>
  <div>
    <b-alert :variant="testResult ? 'success' : 'danger'" show>
      <b-icon :icon="testResult ? 'check-circle-fill' : 'x-circle-fill'"></b-icon> 22.07.2021 13:00 Uhr
    </b-alert>
  </div>
</template>

<script>
export default {
  name: "EntryNote",
  props: {
    testResult: Boolean,
  },
};
</script>

<style scoped></style>
