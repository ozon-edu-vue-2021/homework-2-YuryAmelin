<template>
  <div class="link">
    <h2>{{name}}</h2>
    <h2>{{target}}</h2>
  </div>
</template>

<script>

export default {
  name: "Links",
  props: {
    name: {
      type: String,
      default: ''
    },
    target: {
      type: String,
      default: ''
    },
  },
}
</script>

<style scoped>

</style>