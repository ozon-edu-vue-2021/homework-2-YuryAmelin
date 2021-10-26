<template>
  <div class="folder">
    <div class="info" @click="toggleFolder">
      <img v-if="isOpened" src="../assets/icons/openedDirectory.png" alt="">
      <img v-else src="../assets/icons/closedDirectory.png" alt="">
      <h2>{{name}}</h2>
    </div>
    <h3 v-if="isOpened">Путь: {{myPath}}/{{name}}</h3>
    <div class="level" v-if="isOpened">
      <img class="line" src="../assets/icons/line.png" alt="">
      <div class="elems">
        <folder
            v-for="directory in getDirectories"
            :key="directory.name"
            :name="directory.name"
            :tree="{...directory.contents}"
            :my-path="getPath"
            :directories="getDirectories"
            :files="getFiles"
            :links="getLinks"
        ></folder>
        <file
            v-for="file in getFiles"
            :key="file.name"
            :name="file.name"
        >
        </file>
        <links
            v-for="link in getLinks"
            :key="link.name"
            :name="link.name"
            :target="link.target"
        >
        </links>
      </div>
    </div>
  </div>
</template>

<script>
import Folder from "@/components/Folder";
import File from "@/components/File";
import Links from "@/components/Links";

export default {
  name: "Folder",
  components: {
    Folder,
    File,
    Links
  },
  props: {
    tree: {
      type: Object,
      default: () => ({})
    },
    name: {
      type: String,
      default: ''
    },
    myPath: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: ''
    },
    directories: {
      type: Array,
      default: () => ([])
    },
    files: {
      type: Array,
      default: () => ([])
    },
    links: {
      type: Array,
      default: () => ([])
    },
  },
  methods: {
    toggleFolder() {
      this.isOpened = !this.isOpened
    },
  },
  mounted() {
    this.arrTree = Object.values(this.tree)
  },
  computed: {
    getPath() {
      return `${this.myPath}/${this.name}`
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
    isOpened: false,
    arrTree: [],
  }),
}
</script>

<style scoped>

h2, h3 {
  margin-left: 15px;
}

h3 {
  color: goldenrod;
}

img {
  width: 60px;
  height: 50px;
  margin-right: 5px;
}

.folder {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: left;
  align-items: flex-start;
}

.level {
  display: flex;
}

.info {
  display: flex;
  flex-direction: row;
  cursor: pointer;
}

.elems {
  position: relative;
  left: 100px;
}

.line {
  height: inherit;
}

</style>