<script setup>
import { icons } from '../config'
const { title, more } = defineProps(['title', 'more'])
</script>

<template>
  <div class="main-item">
    <div class="head">
      <div class="title">{{ title }}</div>
      <a 
        class="more" 
        v-if="more" 
        :href="more" 
        v-html="icons.rightSmallUp"
      ></a>
    </div>
    <div class="content"><slot></slot></div>
  </div>
</template>

<style lang="scss">
.main-item {
  margin-bottom: 42px;

  &:last-of-type {
    margin-bottom: 0;
  }

  .head {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .title {
    font-size: 18px;
    font-weight: bold;
    border-radius: 4px;
  }

  .more {
    margin-right: 8px;
    color: var(--font-subtitle-color);

    :hover {
      color: var(--font-color);
    }
  }

  .content {
    padding-top: 12px;
  }
}
</style>
