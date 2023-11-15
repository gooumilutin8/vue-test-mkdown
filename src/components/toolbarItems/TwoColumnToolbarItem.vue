<template>
  <NormalToolbar title="2-columns" @click="handler">
    <template #trigger>
      <span>2 columns</span>
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
      targetValue: `[col-left]${seletedText}[/col-left][col-right][/col-right]`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>