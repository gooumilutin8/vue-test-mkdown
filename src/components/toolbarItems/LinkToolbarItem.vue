<template>
  <NormalToolbar title="link"  @click="handler">
    <template #trigger>
      <span>Link</span>
    </template>
  </NormalToolbar>
</template>

<script setup>
import { NormalToolbar } from 'md-editor-v3';

const props = defineProps({
  insert: {
    type: Function,
    default: () => {}    
  }
})

const handler = () => {
  props.insert((seletedText) => {
    return {
      targetValue: `[${seletedText}](${seletedText})`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>