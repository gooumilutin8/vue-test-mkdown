<template>
  <ImageToolbarItem :insert="insert"  />
  <VideoToolbarItem :insert="insert"  />
  <DescriptionToolbarItem :insert="insert"  />
  <QuoteToolbarItem :insert="insert"  />
  <FootnoteToolbarItem :insert="insert"  />
  <LinkToolbarItem :insert="insert"  />
  <ButtonToolbarItem :insert="insert" />
  <FileToolbarItem :insert="insert" />
  <TwoColumnToolbarItem :insert="insert" />
  <TableToolbarItem :insert="insert" />
  <TableRowToolbarItem :insert="insert" />
</template>

<script setup>
import ButtonToolbarItem from '@/components/toolbarItems/ButtonToolbarItem';
import DescriptionToolbarItem from '@/components/toolbarItems/DescriptionToolbarItem';
import FileToolbarItem from '@/components/toolbarItems/FileToolbarItem';
import FootnoteToolbarItem from '@/components/toolbarItems/FootnoteToolbarItem';
import ImageToolbarItem from '@/components/toolbarItems/ImageToolbarItem';
import LinkToolbarItem from '@/components/toolbarItems/LinkToolbarItem';
import QuoteToolbarItem from '@/components/toolbarItems/QuoteToolbarItem';
import TableRowToolbarItem from '@/components/toolbarItems/TableRowToolbarItem';
import TableToolbarItem from '@/components/toolbarItems/TableToolbarItem';
import TwoColumnToolbarItem from '@/components/toolbarItems/TwoColumnToolbarItem';
import VideoToolbarItem from '@/components/toolbarItems/VideoToolbarItem';

const props = defineProps({
  insert: {
    type: Function,
    default: () => {}
  }
});
</script>