<template>
  <div class="container">
    <h1>アバウトページ</h1>

    <nav>
      <ul>
        <li><NuxtLink to="/">ホーム</NuxtLink></li>
        <li><NuxtLink to="/about">アバウト</NuxtLink></li>
        <li><NuxtLink to="/blog">ブログ</NuxtLink></li>
        <li><NuxtLink to="/contact">お問い合わせ</NuxtLink></li>
      </ul>
    </nav>

    <div class="content">
      <h2>このサイトについて</h2>
      <p>これはNuxt 3のファイルベースルーティング機能を試すためのサンプルプロジェクトです。</p>

      <h3>使用技術</h3>
      <ul>
        <li>Nuxt 3</li>
        <li>Vue 3</li>
        <li>TypeScript</li>
      </ul>

      <h3>ページ構成</h3>
      <ul>
        <li><code>/app/pages/index.vue</code> - ホームページ</li>
        <li><code>/app/pages/about.vue</code> - このページ</li>
        <li><code>/app/pages/blog/index.vue</code> - ブログ一覧</li>
        <li><code>/app/pages/blog/[id].vue</code> - 動的な記事ページ</li>
        <li><code>/app/pages/contact.vue</code> - お問い合わせ</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  font-family: system-ui, sans-serif;
}

h1 {
  color: #00DC82;
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
  color: #00DC82;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border: 1px solid #00DC82;
  border-radius: 4px;
  transition: all 0.3s;
}

nav a:hover {
  background-color: #00DC82;
  color: white;
}

.content {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #f5f5f5;
  border-radius: 8px;
}

code {
  background-color: #e0e0e0;
  padding: 0.2rem 0.4rem;
  border-radius: 3px;
  font-family: monospace;
}

h3 {
  margin-top: 1.5rem;
  color: #333;
}
</style>
