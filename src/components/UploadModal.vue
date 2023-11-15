<template>
  <v-tabs v-model="tab">
    <v-tab value="file">File</v-tab>
    <v-tab value="url">Url</v-tab>
  </v-tabs>
  <v-card-text>
    <v-window v-model="tab">
      <v-window-item value="file">
        <v-text-field type="text" v-model="name" label="File Name" />
        <v-file-input :accept="accept" label="Upload File" v-model="file"></v-file-input>
      </v-window-item>
      <v-window-item value="url">
        <v-text-field type="text" v-model="name" label="File Name" />
        <v-text-field type="url" v-model="url" label="File Url" placeholder="https://example.com" />
      </v-window-item>
    </v-window>
  </v-card-text>
  <v-btn rounded color="medium-emphasis" variant="outlined" @click="handleSubmit">Submit</v-btn>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps ({
  accept: String,
  handle: Function
})
</script>

<script>
export default {
  data: () => {
    return {
      tab: null,
      file: null,
      url: '',
      name: ''
    }
  },
  methods: {
    handleSubmit() {
      if (!this.name) {
        return
      }
      if (this.tab == 'file') {
        if (!this.file) {
          return
        }
        console.log(this.file)
        let reader = new FileReader();
        reader.readAsDataURL(this.file[0]);
        reader.onload = () => {
          const base64 = reader.result
          this.$props.handle(base64, this.name);
        }
      } else {
        if (!this.url) {
          return
        }

        this.$props.handle(this.url, this.name);
      }
    }
  }
}
</script>