<script setup>
const props = defineProps(['findme'])
</script>

<template>
  <div class="find-me__box">
    <a
      class="find-me__item"
      v-for="item in props.findme"
      :href="item.href"
      :key="item.href"
      v-html="item.icon"
    ></a>
  </div>
</template>

<style lang="scss">
.find-me__box {
  color: var(--font-subtitle-color);
  transition: 0.3s color;
}

.find-me__item {
  margin-right: 12px;

  &:hover {
    color: var(--font-color);
  }
}
</style>
