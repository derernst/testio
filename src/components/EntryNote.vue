<template>
  <div>
    <b-alert :variant="entry.result ? 'success' : 'danger'" show>
      <b-icon :icon="entry.result ? 'check-circle-fill' : 'x-circle-fill'"></b-icon> {{entry.date}}
    </b-alert>
  </div>
</template>

<script>
export default {
  name: "EntryNote",
  props: {
    entry: Object,
  }
};
</script>

<style scoped></style>
