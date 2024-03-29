<!-- App.vue -->
<template>
  <div class="app">
    <UserFiles :files="parentFiles"/>
    <MainContent />
    <Sidebar />
  </div>
</template>

<script>
import UserFiles from './components/UserFiles.vue';
import MainContent from './components/MainContent.vue';
import Sidebar from './components/Sidebar.vue';

export default {
  name: 'App',
  components: {
    UserFiles,
    MainContent,
    Sidebar
  },
  data() {
    return {
      showUserFiles: true,
      showSidebar: true,
      parentFiles: [
        { name: 'file1.txt', size: '2MB', dateModified: '2022-01-01' },
        { name: 'file2.txt', size: '3MB', dateModified: '2022-01-02' },
        { name: 'file3.txt', size: '1MB', dateModified: '2022-01-03' },
      ],
    }
  },
  methods: {

  }
}
</script>

<style>
.app {
  display: flex;
  height: 100vh;
  /* change font  */
  font-family: Arial, sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Open Sans';
  background-color: #f8f9fa;
  color: #333;
  margin-top: 50px;

}
</style>










<!-- <template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld :msg="msg"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  computed: {
    msg() {
      return 'Welcome to Your Vue.js App'
    }
  }
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
</style> -->
