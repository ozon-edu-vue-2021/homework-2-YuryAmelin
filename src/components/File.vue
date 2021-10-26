<template>
  <div :class="{file: true, active: selected}" @click="selectFile">
    <img src="../assets/icons/file.png" alt="">
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
  methods: {
    selectFile() {
      this.selected = !this.selected
    }
  },
  data: () => ({
    selected: false
  })
}
</script>

<style scoped>

img {
  width: 40px;
  height: 50px;
  margin-right: 5px;
}

.file {
  display: flex;
  flex-direction: row;
  justify-content: left;
  padding: 5px;
  cursor: pointer;
}

.active {
  border: 4px solid steelblue;
  border-radius: 10px;
  background-color: lightskyblue;
}

</style>