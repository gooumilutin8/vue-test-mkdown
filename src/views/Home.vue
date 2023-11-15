<template>
  <VContainer fluid>
    <VRow>
      <VCol cols="6">
        <MdEditor
          v-model="text"
          language="en-US"
          :footers="[]"
          :preview="false"
          :html-preview="false"
          :toolbars="[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]"
          :show-toolbar-name="true"
          class="md-editor"
        >
          <template #defToolbars>
            <Toolbar/>
          </template>
        </MdEditor>
      </VCol>
      <VCol cols="6">
        <MdPreview v-model="text" />
      </VCol>
    </VRow>
  </VContainer>
</template>

<script setup>
import { ref } from 'vue';
import { MdEditor, MdPreview } from 'md-editor-v3';
import 'md-editor-v3/lib/style.css';
import Toolbar from '@/components/Toolbar.vue';

const text = ref('# Hello World')
</script>

<style scoped="scss">
.md-editor .md-editor-toolbar-item .md-editor-icon{
  display: none;
}
</style>