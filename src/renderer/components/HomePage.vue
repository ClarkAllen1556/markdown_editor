<template>
  <div>
    <div>
      <b-container fluid='xl'>
        <b-row>
          <div>
            <h1>Markdown Editor</h1>
          </div>
        </b-row>
        <b-row>
          <b-col cols="8">
            <Editor v-bind:fm_meta="getFmMeta" />
          </b-col>
          <b-col cols="4">
            <Sidebar v-on:FM_UPDATE="sidebarHandler"/>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
  import Editor from "./Editor.vue";
  import Sidebar from "./Sidebar.vue";

  export default {
    data () {
      return {
        fm_meta: String()
      }
    },
    components: {
      Editor,
      Sidebar
    },
    methods: {
      sidebarHandler(payload) {
        this.fm_meta = `---\n${JSON.stringify(payload.value)}\n---`;
      }
    },
    computed: {
      getFmMeta () {
        return this.fm_meta;
      }
    }
  };
</script>

<style scoped>
  .container-fluid {
    margin-top: 20px;
  }
</style>