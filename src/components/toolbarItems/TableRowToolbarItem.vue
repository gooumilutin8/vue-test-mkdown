<template>
  <NormalToolbar title="table row" @click="handler">
    <template #trigger>
      <span>Table row</span>
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
      targetValue: `[table-row]${seletedText}[/table-row]`,
      select: false,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>