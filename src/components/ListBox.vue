<script setup>
const { list } = defineProps(['list'])
</script>

<template>
  <ul class="list-box">
    <li 
      class="list-item" 
      v-for="item in list" 
      :key="item"
    >{{ item }}</li>
  </ul>
</template>

<style lang="scss">
.list-box {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  list-style: none;
  padding: 0;

  .list-item {
    padding: 4px 8px;
    font-size: 14px;
    color: var(--font-subtitle-color);
    background-color: var(--bg-card-color);
    border-radius: 4px;
    cursor: default;
  }
}
</style>
