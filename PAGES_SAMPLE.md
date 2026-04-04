# Nuxt Pages サンプル

このプロジェクトは、Nuxt 3のファイルベースルーティング機能を試すための複数ページのサンプルです。

## ページ構成

### 静的ルート
- `/` - ホームページ (`pages/index.vue`)
- `/about` - アバウトページ (`pages/about.vue`)
- `/contact` - お問い合わせページ (`pages/contact.vue`)

### ネストされたルート
- `/blog` - ブログ一覧ページ (`pages/blog/index.vue`)
- `/blog/[id]` - 個別記事ページ（動的ルート）(`pages/blog/[id].vue`)

## 動的ルートの例

`pages/blog/[id].vue` は動的ルートの例です。以下のURLでアクセスできます：
- `/blog/1` - 「Nuxt 3を始めよう」
- `/blog/2` - 「ファイルベースルーティング入門」
- `/blog/3` - 「動的ルートの活用方法」

## 機能

### 1. ファイルベースルーティング
`pages/` ディレクトリにVueファイルを配置するだけで、自動的にルーティングが設定されます。

### 2. NuxtLink コンポーネント
各ページには共通のナビゲーションがあり、`<NuxtLink>` を使ってページ間を移動できます。

### 3. レスポンシブデザイン
基本的なスタイリングとホバー効果が実装されています。

## 開発サーバーの起動

```bash
# 依存関係のインストール
pnpm install

# 開発サーバーの起動
pnpm dev
```

開発サーバーが起動したら、ブラウザで `http://localhost:3000` にアクセスしてください。

## 学習ポイント

1. **`app.vue`の役割**: `<NuxtPage />` コンポーネントを使って、ルートに応じたページを表示
2. **静的ルート**: `pages/about.vue` → `/about` のように、ファイル名がURLパスになる
3. **インデックスルート**: `pages/index.vue` → `/` がルートパス
4. **ネストされたルート**: `pages/blog/index.vue` → `/blog`
5. **動的ルート**: `pages/blog/[id].vue` → `/blog/:id` でパラメータを受け取る

## 参考リンク

- [Nuxt 3 ドキュメント - Pages](https://nuxt.com/docs/guide/directory-structure/pages)
- [Nuxt 3 ドキュメント - Routing](https://nuxt.com/docs/getting-started/routing)
