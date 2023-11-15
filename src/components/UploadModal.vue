<template>
  <v-dialog
    width="auto"
    v-model="show"
  >
    <v-card>
      <v-tabs v-model="tab">
        <v-tab value="file">File</v-tab>
        <v-tab value="url">Url</v-tab>
      </v-tabs>
      <v-card-text>
        <v-window v-model="tab">
          <v-window-item value="file">
            <v-file-input :accept="accept" label="Upload File" chips multiple></v-file-input>
          </v-window-item>
          <v-window-item value="url"></v-window-item>
        </v-window>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps ({
  show: Boolean,
  accept: String
})
</script>

<script>
export default {
  data: () => {
    return {
      tab: null
    }
  }
}
</script>