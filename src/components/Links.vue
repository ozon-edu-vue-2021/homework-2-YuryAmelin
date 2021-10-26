<template>
  <div :class="{link: true, active: selected}" @click="selectLink">
    <img src="../assets/icons/link.png" alt="">
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
  methods: {
    selectLink() {
      this.selected = !this.selected
    }
  },
  data: () => ({
    selected: false
  })
}
</script>

<style scoped>

h2 {
  margin: 5px;
}

img {
  width: 40px;
  height: 50px;
  margin-right: 5px;
}

.link {
  display: flex;
  flex-direction: row;
  justify-content: left;
  padding: 5px;
  cursor: pointer;
}

.active {
  border: 4px solid green;
  border-radius: 10px;
  background-color: lightgreen;
}

</style>