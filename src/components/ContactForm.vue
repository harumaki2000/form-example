<template>
  <div class="page-container">
    <div class="form-card">
      <form @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">お名前</label>
          <input type="text" id="name" v-model="name" placeholder="例：佐藤　太郎">
        </div>

        <div class="form-group">
          <label for="email">メールアドレス</label>
          <input type="email" id="email" v-model="email" placeholder="example@example.com">
        </div>

        <div class="form-group">
          <label for="category">質問カテゴリ</label>
          <select id="category" v-model="selectedCategory">
            <option disabled value="">選択してください</option>
            <option value="サービスについて">サービスについて</option>
            <option value="料金について">料金について</option>
            <option value="納期について">納期について</option>
            <option value="その他">その他</option>
          </select>
        </div>

        <div class="form-group" v-if="selectedCategory === 'その他'">
          <label for="other-category">カテゴリ（その他）</label>
          <input type="text" id="other-category" v-model="otherCategoryText" placeholder="具体的なカテゴリを入力">
        </div>

        <div class="form-group">
          <label for="message">質問内容</label>
          <textarea id="message" v-model="message" rows="5" placeholder="質問内容を入力"></textarea>
        </div>

        <button type="submit" class="submit-button">送信</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const name = ref('');
const email = ref('');
const selectedCategory = ref('');
const otherCategoryText = ref('');
const message = ref('');

const handleSubmit = () => {
  console.log(name.value);
  console.log(email.value);
  console.log(selectedCategory.value);
  console.log(otherCategoryText.value);
  console.log(message.value);
}
</script>

<style lang="scss" scoped>
@use "sass:color";

$primary-blue: #007bff;
$input-border-color: #ced4da;
$card-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);

.form-card {
  background-color: #ffffff;
  padding: 32px;
  border-radius: 12px;
  box-shadow: $card-shadow;
  width: 100%;
  max-width: 500px;
  margin: 20px;
}

.form-group {
  margin-bottom: 20px;
  label {
    display: block;
    font-weight: 600;
    margin-bottom: 8px;
    font-size: 14px;
  }
}

input[type="text"],
input[type="email"],
select,
textarea {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid $input-border-color;
  border-radius: 8px;
  font-size: 16px;
  box-sizing: border-box;

  &:focus {
    outline: none;
    border-color: $primary-blue;
    box-shadow: 0 0 0 3px rgba($primary-blue, 0.2);
  }

  &::placeholder {
    color: #999;
  }
}

.submit-button {
  width: 100%;
  padding: 12px 16px;
  background-color: $primary-blue;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease;

  &:hover {
    background-color: color.adjust($primary-blue, $lightness: -10%);
  }

  &:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
}
</style>
