<script setup>
import { icons } from '../config'
const { name, site, repo, desc } = defineProps(['name', 'site', 'repo', 'desc'])
</script>

<template>
  <div class="project-item">
    <div class="project-head">
      <span class="project-name">{{ name }}</span>
      <div class="external">
        <a class="external-item"  v-if="repo" :href="repo" v-html="icons.github"></a>
        <a class="external-item" v-if="site" :href="site" v-html="icons.rightSmallUp"></a>
      </div>
    </div>
    <div class="project-details">
      <div class="project-desc">{{ desc }}</div>
      <slot></slot>
    </div>
  </div>
</template>

<style lang="scss">
.project-item {
  padding: 8px;
  border: 1px solid var(--border-color);
  border-radius: 4px;
  overflow: hidden;
}

.project-name {
  display: inline-block;
  height: 28px;
  line-height: 28px;
  font-size: 18px;
}

.external {
  float: right;
  display: flex;
  align-content: center;
  gap: 8px;
  color: var(--font-subtitle-color);
  transition: color .3s;

  .external-item:hover {
    color: var(--font-color);
  }
}

.project-desc {
  color: var(--font-subtitle-color);
}

.project-details {
  font-size: 14px;
  line-height: 24px;
}
</style>
