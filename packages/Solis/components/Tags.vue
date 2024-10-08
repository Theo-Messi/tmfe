<template>
  <div class="tags">
    <span @click="toggleTag(key)" v-for="(item, key) in data" :key="key" class="tag">
      {{ key }} <strong>{{ data[key].length }}</strong>
    </span>
  </div>
  <div class="tag-header">{{ selectTag }}</div>
  <a
    v-if="selectTag"
    :href="withBase(article.regularPath)"
    v-for="article in data[selectTag]"
    :key="article.regularPath"
    class="posts"
  >
    <div class="post-container">
      <div class="post-dot"></div>
      <div class="post-title">
        <span v-if="article.frontMatter.top" class="top-label">
          <i class="fa-solid fa-fire-flame-simple"></i>
        </span>
        {{ article.frontMatter.title }}
      </div>
    </div>
    <div class="date">{{ article.frontMatter.date }}</div>
  </a>
</template>

<script lang="ts" setup>
import { computed, ref, onMounted } from 'vue'
import { useData, withBase } from 'vitepress'
import { initTags, Post } from '../types/functions'

const { theme } = useData<{ posts: Post[] }>()

// 排序函数，置顶的文章优先
const sortPosts = (posts: Post[]): Post[] => {
  return posts.slice().sort((a, b) => {
    if (a.frontMatter.top && b.frontMatter.top) {
      return new Date(b.frontMatter.date).getTime() - new Date(a.frontMatter.date).getTime()
    }
    if (a.frontMatter.top) return -1
    if (b.frontMatter.top) return 1
    return 0
  })
}

// 对文章数据进行分类并排序
const data = computed<Record<string, Post[]>>(() => {
  const tagData = initTags(theme.value.posts)
  const sortedTagData: Record<string, Post[]> = {}

  for (const key in tagData) {
    sortedTagData[key] = sortPosts(tagData[key])
  }

  return sortedTagData
})

const selectTag = ref('')

// 在组件挂载时从 URL 中获取初始 tag
onMounted(() => {
  selectTag.value = new URLSearchParams(location.search).get('tag') || ''
})

const toggleTag = (tag: string) => {
  selectTag.value = tag
}
</script>

<style lang="scss" scoped>
.tags {
  margin-top: 14px;
  display: flex;
  flex-wrap: wrap;
}

.tag {
  display: inline-block;
  padding: 4px 16px;
  margin: 6px 8px;
  font-size: 0.875rem;
  line-height: 25px;
  background-color: var(--vp-c-bg-alt);
  transition: background-color 0.4s ease;
  border-radius: 2px;
  color: var(--vp-c-text-1);
  cursor: pointer;

  strong {
    color: var(--vp-c-brand);
  }
}

.tag-header {
  font-size: 1.5rem;
  font-weight: 500;
  margin: 1rem 0;
  text-align: left;
}
</style>
