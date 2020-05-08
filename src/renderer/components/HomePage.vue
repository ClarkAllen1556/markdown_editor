<template>
  <b-container fluid="xl">
    <b-row>
      <div>
        <h1>Markdown Editor</h1>
      </div>
    </b-row>
    <b-row>
      <b-col class="b-col" cols="8">
        <Editor v-bind:fm_meta="getFmMeta" v-bind:load_file="loadFile"/>
      </b-col>
      <b-col class="b-col" cols="4">
        <Sidebar v-on:FM_UPDATE="fmHandler" v-on:P_OPEN_LOCAL="pLoadHandler"/>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  import Editor from "./Editor.vue";
  import Sidebar from "./Sidebar.vue";

  export default {
    data() {
      return {
        fm_meta: String(),
        loadFile: String()
      };
    },
    components: {
      Editor,
      Sidebar
    },
    methods: {
      fmHandler(payload) {
        this.fm_meta = `---\n${JSON.stringify(payload.value)}\n---\n`;
      },

      pLoadHandler(payload) {
        const { dialog } = require("electron").remote;
        const fs = require('fs');

        dialog.showOpenDialog().then( (file) => {
          if (file.canceled) throw new Error("Error loading file: Canceled by user.");

          return fs.readFileSync(file.filePaths[0], 'utf-8')
        }).then( (readData) => {
          this.loadFile = readData;
        }).catch( (e) => {
          console.error(e);
        })
      }
    },
    computed: {
      getFmMeta() {
        return this.fm_meta;
      },

      sendLoadedFile() {
        return this.loadFile;
      }
    }
  };
</script>

<style scoped lang="scss">
@import "~bootstrap";

.b-col {
  @extend .border;
  @extend .rounded;
  @extend .p-1;
  height: 750px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}
</style>