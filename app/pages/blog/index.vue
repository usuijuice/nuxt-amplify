<template>
  <div class="container">
    <h1>ブログ一覧</h1>

    <nav>
      <ul>
        <li><NuxtLink to="/">ホーム</NuxtLink></li>
        <li><NuxtLink to="/about">アバウト</NuxtLink></li>
        <li><NuxtLink to="/blog">ブログ</NuxtLink></li>
        <li><NuxtLink to="/contact">お問い合わせ</NuxtLink></li>
      </ul>
    </nav>

    <div class="content">
      <h2>最新記事</h2>
      <div class="blog-list">
        <article v-for="post in posts" :key="post.id" class="blog-item">
          <h3>
            <NuxtLink :to="`/blog/${post.id}`">{{ post.title }}</NuxtLink>
          </h3>
          <p class="date">{{ post.date }}</p>
          <p>{{ post.excerpt }}</p>
        </article>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const posts = [
  {
    id: 1,
    title: 'Nuxt 3を始めよう',
    date: '2026-04-01',
    excerpt: 'Nuxt 3の基本的な使い方とセットアップ方法について紹介します。'
  },
  {
    id: 2,
    title: 'ファイルベースルーティング入門',
    date: '2026-04-02',
    excerpt: 'pagesディレクトリを使った直感的なルーティング設定を学びます。'
  },
  {
    id: 3,
    title: '動的ルートの活用方法',
    date: '2026-04-03',
    excerpt: '[id].vueを使った動的なページ生成の実装方法を解説します。'
  }
]
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

.blog-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.blog-item {
  padding: 1.5rem;
  background-color: #f5f5f5;
  border-radius: 8px;
  transition: transform 0.2s;
}

.blog-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.blog-item h3 {
  margin: 0 0 0.5rem 0;
}

.blog-item h3 a {
  color: #333;
  text-decoration: none;
}

.blog-item h3 a:hover {
  color: #2563EB;
}

.date {
  color: #666;
  font-size: 0.9rem;
  margin: 0.5rem 0;
}
</style>
