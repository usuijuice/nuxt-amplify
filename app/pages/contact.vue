<template>
  <div class="container">
    <h1>お問い合わせ</h1>

    <nav>
      <ul>
        <li><NuxtLink to="/">ホーム</NuxtLink></li>
        <li><NuxtLink to="/about">アバウト</NuxtLink></li>
        <li><NuxtLink to="/blog">ブログ</NuxtLink></li>
        <li><NuxtLink to="/contact">お問い合わせ</NuxtLink></li>
      </ul>
    </nav>

    <div class="content">
      <form @submit.prevent="handleSubmit" class="contact-form">
        <div class="form-group">
          <label for="name">お名前</label>
          <input
            id="name"
            v-model="formData.name"
            type="text"
            required
            placeholder="山田太郎"
          >
        </div>

        <div class="form-group">
          <label for="email">メールアドレス</label>
          <input
            id="email"
            v-model="formData.email"
            type="email"
            required
            placeholder="example@example.com"
          >
        </div>

        <div class="form-group">
          <label for="message">メッセージ</label>
          <textarea
            id="message"
            v-model="formData.message"
            rows="5"
            required
            placeholder="お問い合わせ内容をご記入ください"
          ></textarea>
        </div>

        <button type="submit" class="submit-btn">送信</button>

        <p v-if="submitted" class="success-message">
          お問い合わせありがとうございます！（これはデモです）
        </p>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
const formData = reactive({
  name: '',
  email: '',
  message: ''
})

const submitted = ref(false)

const handleSubmit = () => {
  console.log('Form submitted:', formData)
  submitted.value = true

  // デモ用：3秒後にリセット
  setTimeout(() => {
    submitted.value = false
    formData.name = ''
    formData.email = ''
    formData.message = ''
  }, 3000)
}
</script>

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
}

.contact-form {
  background-color: #f5f5f5;
  padding: 2rem;
  border-radius: 8px;
}

.form-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: #333;
}

input,
textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
  font-family: inherit;
  box-sizing: border-box;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #00DC82;
}

.submit-btn {
  background-color: #00DC82;
  color: white;
  border: none;
  padding: 0.75rem 2rem;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.submit-btn:hover {
  background-color: #00c374;
}

.success-message {
  margin-top: 1rem;
  padding: 1rem;
  background-color: #d4edda;
  color: #155724;
  border-radius: 4px;
  text-align: center;
}
</style>
