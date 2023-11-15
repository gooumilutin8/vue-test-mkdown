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
        <MdPreview v-model="text" :sanitize="sanitizeHtml" />
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

const sanitizeHtml = (html) => {
  let newHtml = html
  
  const colRegex = /\[col\-left\](.*?)\[\/col\-left\]\[col\-right\](.*?)\[\/col\-right\]/gm;
  const matches = [...html.matchAll(colRegex)][0];
  if (matches) {
    for (let i = 0; i < matches.length; i += 3) {
      newHtml = newHtml.replace(matches[i], `
      <div class="v-row">
        <div class="v-col v-col-6">${matches[i+1] || ''}</div>
        <div class="v-col v-col-6">${matches[i+2] || ''}</div>
      </div>
      `)
    }
  }
  return newHtml;
}
</script>
