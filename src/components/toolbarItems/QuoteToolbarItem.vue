<template>
  <NormalToolbar title="quote" @click="handler">
    <template #trigger>
      <span>Quote</span>
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
      targetValue: `> ${seletedText}`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>