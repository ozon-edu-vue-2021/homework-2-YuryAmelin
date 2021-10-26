<template>
  <div class="file">
    <h2>{{name}}</h2>
    </div>
</template>

<script>

export default {
  name: "File",
  props: {
    name: {
      type: String,
      default: ''
    },
  },
}
</script>

<style scoped>

</style>