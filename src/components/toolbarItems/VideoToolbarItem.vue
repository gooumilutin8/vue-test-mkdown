<template>
  <ModalToolbar
    title="video"
    modal-title="Upload Video"
    :visible="visible"
    @click="visible = true"
    @close="visible = false"
    width="600px"
    height="400px"
  >
    <template #trigger>
      <span>Video</span>
    </template>
    <template #default>
      <UploadModal
        accept="video/*"
        :handle="handler"
      />
    </template>
  </ModalToolbar>
</template>

<script setup>
import { ref } from 'vue';
import { ModalToolbar } from 'md-editor-v3';
import UploadModal from '../UploadModal.vue';

const visible = ref(false);

const props = defineProps({
  insert: {
    type: Function,
    default: () => {}    
  }
})

const handler = (video, name) => {
  visible.value = false;
  props.insert((seletedText) => {
    return {
      targetValue: `<video width="320" height="240" controls>
  <source src="${video}">
</video>`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>