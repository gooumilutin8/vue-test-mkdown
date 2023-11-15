<template>
  <ModalToolbar
    title="image"
    modal-title="Upload Image"
    :visible="visible"
    @click="visible = true"
    @close="visible = false"
    width="600px"
    height="400px"
  >
    <template #trigger>
      <span>Image</span>
    </template>
    <template #default>
      <UploadModal
        accept="image/*"
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

const handler = (image, name) => {
  visible.value = false;
  props.insert((seletedText) => {
    return {
      targetValue: `![${name}](${image})`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>