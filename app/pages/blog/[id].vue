<template>
  <div class="container">
    <h1>{{ post?.title }}</h1>

    <nav>
      <ul>
        <li><NuxtLink to="/">ホーム</NuxtLink></li>
        <li><NuxtLink to="/about">アバウト</NuxtLink></li>
        <li><NuxtLink to="/blog">ブログ</NuxtLink></li>
        <li><NuxtLink to="/contact">お問い合わせ</NuxtLink></li>
      </ul>
    </nav>

    <div class="content">
      <p class="date">{{ post?.date }}</p>
      <div class="article-body">
        <p>{{ post?.content }}</p>
      </div>

      <div class="back-link">
        <NuxtLink to="/blog">← ブログ一覧に戻る</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const route = useRoute()
const id = computed(() => route.params.id)

// サンプルデータ
const posts = {
  '1': {
    id: 1,
    title: 'Nuxt 3を始めよう',
    date: '2026-04-01',
    content: 'Nuxt 3は、Vue.jsベースのフルスタックフレームワークです。ファイルベースルーティング、サーバーサイドレンダリング、静的サイト生成など、多くの機能を提供しています。このチュートリアルでは、Nuxt 3の基本的な使い方とセットアップ方法について詳しく紹介します。'
  },
  '2': {
    id: 2,
    title: 'ファイルベースルーティング入門',
    date: '2026-04-02',
    content: 'Nuxt 3では、pagesディレクトリにVueファイルを配置するだけで、自動的にルーティングが設定されます。この直感的な仕組みにより、開発者はルーター設定を手動で行う必要がなく、より効率的に開発を進めることができます。'
  },
  '3': {
    id: 3,
    title: '動的ルートの活用方法',
    date: '2026-04-03',
    content: '角括弧を使った[id].vueのようなファイル名により、動的なルートパラメータを受け取ることができます。これにより、ブログ記事やユーザープロフィールページなど、パラメータに応じてコンテンツが変わるページを簡単に実装できます。'
  }
}

const post = computed(() => posts[id.value as keyof typeof posts])
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  font-family: system-ui, sans-serif;
}

h1 {
  color: #2563EB;
  margin-bottom: 1rem;
}

nav ul {
  list-style: none;
  padding: 0;
  display: flex;
  gap: 1rem;
  margin: 2rem 0;
}

nav a {
  color: #2563EB;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border: 1px solid #2563EB;
  border-radius: 4px;
  transition: all 0.3s;
}

nav a:hover {
  background-color: #2563EB;
  color: white;
}

.content {
  margin-top: 2rem;
}

.date {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 1.5rem;
}

.article-body {
  padding: 2rem;
  background-color: #f5f5f5;
  border-radius: 8px;
  line-height: 1.6;
}

.back-link {
  margin-top: 2rem;
}

.back-link a {
  color: #2563EB;
  text-decoration: none;
}

.back-link a:hover {
  text-decoration: underline;
}
</style>
