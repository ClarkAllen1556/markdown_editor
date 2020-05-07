<template>
  <div>
    <b-tabs content-class="mt-3">
      <b-tab title="Front Matter" active>
        <p>I'm the first tab</p>
      </b-tab>
      <b-tab title="Posts">
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
  import { TabsPlugin } from "bootstrap-vue";
  import Vue from "vue";
  Vue.use(TabsPlugin);

  export default {
    name: "sidebar"
  };
</script>

<style>
</style>