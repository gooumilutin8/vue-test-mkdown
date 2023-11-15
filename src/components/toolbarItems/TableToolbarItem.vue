<template>
  <NormalToolbar title="table" @click="handler">
    <template #trigger>
      <span>Table</span>
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
      targetValue: `[table]${seletedText}[/table]`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>