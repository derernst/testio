<template>
  <div>
      <b-icon
        :icon="entry.result ? 'check-circle-fill' : 'x-circle-fill'"
        :variant="entry.result ? 'success' : 'danger'"
      ></b-icon>
      <span class="pl-3">{{ entry.date }}</span>
  </div>
</template>

<script>
export default {
  name: "EntryNote",
  props: {
    entry: Object,
  },
};
</script>
