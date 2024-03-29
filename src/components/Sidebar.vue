<!-- Sidebar.vue -->
<template>
    <div class="sidebar" :class="{ 'collapsed': isCollapsed }">
        <button class="btn-settings" @click="toggle">Settings</button>
        <div class="settings-item-area" v-show="!isCollapsed">
            <div>
                <label>Speed: </label>
                <input type="range" min="0" max="2" step="0.25" />
            </div>
            <div>
                <label>Reader: </label>
                <select id="select_reader_id">
                    <option>Reader 1</option>
                    <option>Reader 2</option>
                </select>
            </div>
            <div>
                <label>Language: </label>
                <select id="select_language_id">
                    <option>English</option>
                    <option>Chinese</option>
                    <option>Vietnamese</option>
                </select>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'side-bar',
    data() {
        return {
            isCollapsed: false
        }
    },
    methods: {
        toggle() {
            this.isCollapsed = !this.isCollapsed;
        }
    }
}
</script>

<style scoped>
.sidebar {
    padding-left: 10px;
    font-size: 16px;
    padding-top: 10px;
    margin-left: 15px;
    width: 250px;
    overflow: auto;
    transition: width 0.3s ease;
    border-left: 1px solid rgba(0, 110, 255, 0.397);
}

.sidebar.collapsed {
    width: 50px;
}

.btn-settings {
    font-size: large;
    background-color: #edeff1;
    color: rgb(0,120,212);
    border: none;
    padding: 5px 10px;
    cursor: pointer;
    margin-bottom: 10px;
    width: 90%;
    height: 50px;
}

.settings-item-area > div {
  margin-bottom: 20px;
}

.sidebar button:hover {
    background-color: rgba(92, 124, 150, 0.274);
}
</style>