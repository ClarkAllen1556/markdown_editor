<template>
  <div>
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
        <b-button v-b-toggle.posts>[post info]</b-button>
        <b-collapse id="posts">
          <b-card>
            <p>hello there! i'm post info</p>
          </b-card>
        </b-collapse>
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
  import FmForm from "./FrontmatterForm";

  export default {
    name: "Sidebar",
    props: {

    },
    components: {
      FmForm
    },
    methods: {
      fmFormHandle (fm_payload) {
        console.info(JSON.stringify(fm_payload));

        this.$emit("FM_UPDATE", fm_payload)
      }
    }
  };
</script>

<style>
</style>