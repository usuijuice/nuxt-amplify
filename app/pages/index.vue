<template>
  <div class="container">
    <h1>ホームページ</h1>
    <p>Nuxt Pagesのサンプルへようこそ！</p>

    <nav>
      <ul>
        <li><NuxtLink to="/">ホーム</NuxtLink></li>
        <li><NuxtLink to="/about">アバウト</NuxtLink></li>
        <li><NuxtLink to="/blog">ブログ</NuxtLink></li>
        <li><NuxtLink to="/contact">お問い合わせ</NuxtLink></li>
      </ul>
    </nav>

    <div class="content">
      <h2>機能</h2>
      <ul>
        <li>ファイルベースルーティング</li>
        <li>動的ルート</li>
        <li>ネストされたルート</li>
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
  color: #F5C300;
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
  color: #F5C300;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border: 1px solid #F5C300;
  border-radius: 4px;
  transition: all 0.3s;
}

nav a:hover {
  background-color: #F5C300;
  color: white;
}

.content {
  margin-top: 2rem;
  padding: 1rem;
  background-color: #f5f5f5;
  border-radius: 8px;
}
</style>
