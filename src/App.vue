<template>
  <div id="app">
    <folder
        :tree="{...tree.contents}"
        :name="tree.name"
        :type="tree.type"
        :my-path="getPath"
        :directories="getDirectories"
        :files="getFiles"
        :links="getLinks"
    ></folder>
  </div>
</template>

<script>
import tree from '../public/static/node_modules.json'
import Folder from "@/components/Folder";

export default {
  name: 'App',
  components: {
    Folder
  },
  mounted() {
    this.arrTree = [...this.tree.contents]
  },
  computed: {
    getPath() {
      return ``
    },
    getDirectories() {
      return this.arrTree.filter(el => el.type === 'directory')
    },
    getFiles() {
      return this.arrTree.filter(el => el.type === 'file')
    },
    getLinks() {
      return this.arrTree.filter(el => el.type === 'link')
    },
  },
  data: () => ({
    arrTree: [],
    tree
}),
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: 90vh;
  overflow: scroll;
  display: flex;
}
</style>
