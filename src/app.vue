<script setup>
import ToggleTheme from './components/ToggleTheme.vue'
import FindMeBox from './components/FindMeBox.vue'
import MainItem from './components/MainItem.vue'
import ProjectItem from './components/ProjectItem.vue'
import ListBox from './components/ListBox.vue'

import config from './config.js'

// prettier-ignore
const { 
  name, 
  email, 
  profession, 
  about, 
  findme, 
  projects, 
  skills, 
  languages 
} = config
</script>

<template>
  <ToggleTheme class="right-top"></ToggleTheme>

  <div class="layout">
    <div class="sidebar">
      <h1>{{ name }}</h1>
      <p class="work">{{ profession }}</p>
      <a class="email" :href="'mailto:'.concat(email)">
        {{ email }}
      </a>
      <FindMeBox :findme="findme"></FindMeBox>
    </div>

    <main>
      <MainItem title="关于">{{ about }}</MainItem>
      <MainItem title="项目" more="https://github.com/2113ic?tab=repositories">
        <div class="project-container">
          <ProjectItem
            v-for="project in projects"
            :name="project.name"
            :key="project.name"
            :site="project.site"
            :repo="project.repo"
            :desc="project.desc"
          >
            <template v-if="project.name === 'Dot'">
              <ul>
                <li>HtmlPlus 通过实现类似vue的指令增强原生开发体验</li>
                <li>Pagination 分页器</li>
                <li>FormValidator 表单验证器</li>
                <li>TabSwitcher Tab切换器</li>
                <li>LightTip 轻提示</li>
                <li>Banner 轮播图</li>
              </ul>
            </template>

            <template v-if="project.name === '个人博客'">
              <p>技术栈：Astro、Vue、Sass</p>
              <p>实现效果：</p>
              <ul>
                <li>可通过配置文件快速应用博客内容</li>
                <li>博客文章展示、个人项目展示</li>
              </ul>
            </template>

            <template v-if="project.name === '线上售药'">
              <p>负责前台、后台界面编写；负责编写采集数据脚本。</p>
              <p>实现：</p>
              <ul>
                <li>使用 class 语法糖让业务代码模块化</li>
                <li>封装 fetch 集中管理后端接口</li>
                <li>封装 Cookie 基本操作对象</li>
              </ul>
            </template>
          </ProjectItem>
        </div>
      </MainItem>
      <MainItem title="教育经历">
        <div class="education-row">
          <span>本科</span>
          <span>2020/9-2024/7</span>
        </div>
        <div class="education-row grey">
          <span>广东白云学院</span>
          <span>信息管理与信息系统</span>
        </div>
      </MainItem>
      <MainItem title="技能">
        <ListBox :list="skills"></ListBox>
      </MainItem>
      <MainItem title="语言">
        <ListBox :list="languages"></ListBox>
      </MainItem>
    </main>
  </div>
  <footer>
    <a
      class="order-version"
      href="https://github.com/2113ic/resume/raw/master/public/resume.pdf"
      download
    >
      PDF Version
    </a>
  </footer>
</template>

<style lang="scss">
.right-top {
  position: absolute;
  right: 24px;
  top: 24px;
}

.layout {
  display: flex;
  flex-direction: row-reverse;
  gap: 100px;
  max-width: 900px;
  margin: 64px auto 24px;
}

@media (max-width: 960px) {
  .layout {
    gap: 42px;
    flex-direction: column;
    padding: 0 24px;
  }
}

svg {
  vertical-align: bottom;
}

.grey {
  color: var(--font-subtitle-color);
}

.sidebar {
  h1 {
    margin: 0;
    font-size: 22px;
  }

  .work,
  .email {
    margin: 0.5em 0;
    font-size: 14px;
    color: var(--font-subtitle-color);
  }

  .email {
    display: inline-block;
    margin-bottom: 16px;
    border-bottom: 2px dashed var(--border-color);
    cursor: pointer;
  }
}

main {
  .project-container {
    display: grid;
    gap: 12px;
    grid-template-columns: 1fr 1fr;
  }

  @media (max-width: 640px) {
    .project-container {
      grid-template-columns: 1fr;
    }
  }

  .education-row {
    display: flex;
    justify-content: space-between;
    line-height: 28px;
  }
}

footer {
  line-height: 48px;
  text-align: center;

  .order-version {
    color: var(--font-subtitle-color);
    border-bottom: 2px dashed var(--border-color);
  }
}
</style>
