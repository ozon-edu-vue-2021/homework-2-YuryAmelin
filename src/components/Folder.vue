<template>
  <div class="directories" v-if="directories">
    <h2 @click="toggleFolder">{{name}}</h2>
    <div v-if="isOpened">
      <folder
          v-for="folder in updateDirectories"
          :key="folder.name"
          :name="folder.name"
          :tree="{...folder.contents}"
          :directories="updateDirectories"
          :files="updateFiles"
          :links="updateLinks"
      ></folder>
      <file
          v-for="file in updateFiles"
          :key="file.name"
          :name="file.name"
      >
      </file>
      <links
          v-for="link in updateLinks"
          :key="link.name"
          :name="link.name"
          :target="link.target"
      >
      </links>
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
    }
  },
  mounted() {
    this.arrTree = Object.values(this.tree)
  },
  computed: {
    updateDirectories() {
      return this.arrTree.filter(el => el.type === 'directory')
    },
    updateFiles() {
      return this.arrTree.filter(el => el.type === 'file')
    },
    updateLinks() {
      return this.arrTree.filter(el => el.type === 'link')
    },
  },
  data: () => ({
    isOpened: false,
    arrTree: []
  })
}
</script>

<style scoped>

.mainTree {
  display: flex;
  flex-direction: column;
  margin: 2px;
}

</style>