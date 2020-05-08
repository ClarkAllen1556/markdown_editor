<template>
  <div>
    <b-form v-on:submit.prevent="submit" v-on:reset.prevent="clear">
      <b-form-group
        id="title-meta"
        label="Post Title"
        label-for="title-input"
        description="Public title for your post."
      >
        <b-form-input
          id="title-input"
          v-model="form.title"
          type="text"
          required
          placeholder="Make it a good one!"
        ></b-form-input>
      </b-form-group>

      <b-form-group
        id="author-meta"
        label="Author:"
        label-for="author-input"
        description="Author's name"
      >
        <b-form-input
          id="author-input"
          v-model="form.author"
          type="text"
          required
          placeholder="Who wrote this?"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="description-meta" label="Description" label-for="desc-input">
        <b-form-textarea
          id="desc-input"
          placeholder="A good summary!"
          v-model="form.description"
          rows="3"
          max-rows="6"
          required
          no-resize
        />
      </b-form-group>

      <b-form-group id="date-meta" label="Date this post was written." label-for="date-input">
        <b-form-datepicker id="date-meta" v-model="form.date" required />
      </b-form-group>

      <b-form-group
        id="type-meta"
        label="Draft or Publish?"
        label-for="dp-check"
      >
        <template v-slot:description>
          <b-form-invalid-feedback v-bind:state="state">Post will be flagged as "DRAFT"</b-form-invalid-feedback>
          <b-form-valid-feedback v-bind:state="state">Post will be flagged as "Publish"</b-form-valid-feedback>
        </template>
        <b-form-checkbox-group
          id="dp-check"
          v-bind:options="options"
          v-bind:state="state"
          v-model="publish"
          switches
        />
      </b-form-group>

      <b-button id="submitBtn" type="submit" variant="primary">Apply frontmatter</b-button>
      <b-button id="clearBtn" type="reset" variant="danger">Clear input</b-button>
    </b-form>
  </div>
</template>

<script>
  export default {
    name: "FmForm",
    data() {
      return {
        form: {
          title: String(),
          author: String(),
          description: String(),
          date: Date(),
          type: String()
        },
        options: [{ text: "Publish", value: "article" }],
        publish: []
      };
    },
    methods: {
      submit() {
        const { ipcRenderer, remote }= require('electron');

        if (this.publish[0] === "article") this.form.type = "article";
        else this.form.type = "draft";

        let fm_value = this.form;

        this.$emit("FM_APPLIED", fm_value);
      },

      clear() {
        this.form.title = "";
        this.form.author = "";
        this.form.description = "";
        this.form.date = "";
        this.form.type = "";

        this.publish = [];
        this.$emit("FM_CLEARED");
      }
    },
    computed: {
      state() {
        return this.publish[0] === "article" ? true : false;
      }
    }
  };
</script>

<style>
</style>