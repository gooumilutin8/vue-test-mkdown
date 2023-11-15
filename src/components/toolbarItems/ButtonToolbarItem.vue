<template>
  <NormalToolbar title="button" @click="handler">
    <template #trigger>
      <span>Button</span>
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
      targetValue: `[button]${seletedText}[/button]`,
      select: true,
      deviationStart: 0,
      deviationEnd: 0
    }
  })
}
</script>