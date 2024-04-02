<!-- MainContent.vue -->
<template>
    <div class="main-content">
        <div class="row">
            <button class="btn-add-file" @click="showModal = true">+</button>
            <button class="btn-file">Select File</button>
            <button class="btn-file">Save</button>
        </div>
        <div class="row">
            <button class="btn-audio btn-play" @mousedown.prevent="playSelectedText">&#9658;</button>
            <button class="btn-audio btn-pause">&#9616;&#9616;</button>
            <input class="audio-range" type="range" min="0" max="totalAudioTime" step="1" v-model="audioTime" />
            <select>
                <option>Frequency 1</option>
                <option>Frequency 2</option>
            </select>
        </div>
        <div class="row">
            <textarea id="input_area" placeholder="Enter text here..." v-model="inputText"></textarea>
        </div>
        <!-- popup show select add file -->
        <div v-if="showModal" class="modal" @click.self="showModal = false">
            <div class="modal-content">
                <button @click="addFolder">
                    Thêm thư mục
                </button>
                <button @click="addFile">
                    Thêm file
                </button>
                <button @click="showModal = false">
                    Đóng
                </button>
            </div>
        </div>
        <!-- end popup select add file -->
    </div>
</template>

<script>
export default {
    name: 'MainContent',
    data() {
        return {
            audioTime: 0,
            showModal: false,
            totalAudioTime: 100,
            audioInterval: null,
            selectedText: '', // selected text in textarea
            inputText: '', // text in textarea
        }
    },
    methods: {
        addFile() {
            this.files.push('New File');
            this.showModal = false;
        },
        removeFile(index) {
            this.files.splice(index, 1);
        },
        addFolder() {
            this.files.push('New Folder');
            this.showModal = false;
        },
        deleteFolder(index) {
            this.files.splice(index, 1);
        },
        playSelectedText() {
            // function call api text to speech
            const textarea = document.getElementById('input_area');
            if (textarea.selectionStart !== textarea.selectionEnd) {
                this.selectedText = this.inputText.substring(textarea.selectionStart, textarea.selectionEnd);
                console.log(this.selectedText);

                // Call api to get speech
                const audioDuration = callTextToSpeechAPI(this.selectedText);
                // Update audioTime every second
                this.totalAudioTime = audioDuration;
                this.audioInterval = setInterval(() => {
                    if (this.audioTime < this.totalAudioTime) {
                        this.audioTime++;
                    } else {
                        clearInterval(this.audioInterval);
                    }
                }, 1000);
            }
        }
    }
}
</script>

<style scoped>
.main-content {
    flex-grow: 1;
    overflow: auto;
}

.row {
    display: flex;
    /* Add this line */
    margin-bottom: 10px;
}

.row .btn-audio {
    color: rgb(73, 178, 237);
    border: 1px solid rgb(73, 178, 237);
    width: 35px;
    height: 35px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    cursor: pointer;
    margin-right: 5px;
}

.row .btn-audio.btn-play {
    background-color: white;
}

.row .btn-audio.btn-pause {
    background-color: white;
}

.row .audio-range {
    width: 50%;
    margin-right: 50px;
}

.row textarea {
    font-size: 20px;
    width: 100%;
    height: 680px;
    padding: 10px 10px;
    border: 1px solid rgba(0, 110, 255, 0.418);
}

.btn-file {
    background-color: #edeff1;
    color: rgb(0, 120, 212);
    border: none;
    cursor: pointer;
    margin-right: 10px;
    width: 80px;
    height: 40px;
}

.row button:hover {
    background-color: rgba(92, 124, 150, 0.274);
}

.btn-add-file {
    font-size: 35px;
    background-color: #edeff1;
    color: rgb(0, 120, 212);
    border: none;
    cursor: pointer;
    margin-right: 10px;
    width: 40px;
    height: 40px;
    text-align: center;
}
</style>

<style popup>
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

.modal-content {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    flex-direction: column;
    display: flex;

}

.modal-content button {
    background-color: #edeff1;
    color: rgb(0, 120, 212);
    border: none;
    cursor: pointer;
    margin-right: 10px;
    width: 200px;
    height: 40px;
    margin: 5px;
    font-size: medium;
    font-weight: bold;
}
</style>