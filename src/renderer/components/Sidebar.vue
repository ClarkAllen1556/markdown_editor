<template>
  <b-tabs content-class="mt-3">
    <b-tab active>
      <template v-slot:title>
        <b-icon icon="file-earmark-code" />
        Frontmatter
      </template>
      <FmForm v-on:FM_UPDATE="fmFormHandle" />
    </b-tab>
    <b-tab>
      <template v-slot:title>
        <b-icon icon="newspaper" />
        Posts
      </template>
      <b-button variant="primary" v-on:click="$emit('P_OPEN_LOCAL')"> Open </b-button>
      <b-button v-b-toggle.posts>[post info]</b-button>
      <b-collapse id="posts">
        <b-card>
          <p>hello there! i'm post info</p>
        </b-card>
      </b-collapse>
    </b-tab>
    <b-tab>
      <template v-slot:title>
        <b-icon icon="box-arrow-in-up-right" />
        Push
      </template>
      <b-button v-on:click="pushPost">
        Push
      </b-button>
    </b-tab>
  </b-tabs>
</template>

<script>
  import FmForm from "./FrontmatterForm";

  export default {
    name: "Sidebar",
    props: {},
    components: {
      FmForm
    },
    methods: {
      fmFormHandle(fm_payload) {
        console.info(JSON.stringify(fm_payload));

        this.$emit("FM_UPDATE", fm_payload);
      },
      async pushPost () {
        const simpleGit = require("simple-git/promise")("../../../_local_posts/.");

        await simpleGit.branch()
        await simpleGit.init()
        await simpleGit.add("./*")
        await simpleGit.addRemote('origin', 'git@github.com:ClarkAllen1556/basic_vue_blog.git')
        await simpleGit.push(['-u', 'origin', 'master']);
        console.log("done")
      }
    }
  };
</script>

<style scoped lang="scss">
@import '~bootstrap';

</style>