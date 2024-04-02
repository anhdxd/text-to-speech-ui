<!-- UserFiles.vue -->
<template>
  <div class="user-files" :class="{ 'collapsed': isCollapsed }">
    <button class="btn-all-file" @click="toggle">All files</button>
    <ul class="no-bullets" v-show="!isCollapsed" style="margin-top: 30px;">
      <li v-for="(file, index) in files" :key="index">
        <button class="full-width-button">{{ file.name }}</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserFiles',
  props: {
    files: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      showModal: false,
      isCollapsed: false,
    }
  },
  methods: {
    toggle() {
      this.isCollapsed = !this.isCollapsed;
    },
  },
}
</script>

<style scoped>
.user-files {
  padding-top: 10px;
  margin-right: 15px;
  width: 150px;
  overflow: auto;
  border-right: 1px solid rgba(0, 110, 255, 0.445);
  transition: width 0.3s ease;
}

.user-files.collapsed {
  width: 50px;
}
.btn-all-file {
  font-size: large;
  width: 90%;
  height: 50px;
  background-color: #edeff1;
  color: rgb(0,120,212);
  border: none;
  cursor: pointer;
  margin-left: 5px;
}

.user-files button:hover {
    background-color: rgba(92, 124, 150, 0.274);
}

.no-bullets {
  list-style-type: none;
  padding-left: 10px;
  max-height: max-content;
  overflow-y: auto;
}
.full-width-button {
  width: 90%;
  height: 50px;
  background-color: #edeff1;
  color: rgb(0,120,212);
  border: none;
  cursor: pointer;
  margin-bottom: 3px;
}

</style>