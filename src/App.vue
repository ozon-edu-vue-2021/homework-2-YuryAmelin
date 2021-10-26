<template>
  <div id="app">
    <folder
        :tree="{...mainTree.contents.slice(0, 5)}"
        :name="mainTree.name"
        :type="mainTree.type"
        :directories="directories"
        :files="files"
        :links="links"
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
    const arr = [...this.mainTree.contents.slice(0, 5)]
    arr.forEach(subTree => {
      if (subTree.type === 'directory') {
        this.directories.push(subTree)
      } else if (subTree.type === 'file') {
        this.files.push(subTree)
      } else {
        this.links.push(subTree)
      }
    })
  },
  data: () => ({
    mainTree: tree,
    directories: [],
    files: [],
    links: []
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
}
</style>
