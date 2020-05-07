<template>
  <div>
    <b-tabs content-class="mt-3">
      <b-tab active>
        <template v-slot:title>
          <b-icon icon="file-earmark-code" />
          Frontmatter
        </template>
        <FmForm />
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
    components: {
      FmForm
    }
  };
</script>

<style>
</style>