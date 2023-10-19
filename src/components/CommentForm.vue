<template>
  <div class="comment-form">
    <form @submit.prevent="submitComment">
      <label for="name">Имя:</label>
      <input type="text" id="name" v-model="newComment.name" required>

      <label for="text">Текст ответа:</label>
      <textarea id="text" v-model="newComment.text" required></textarea>

      <label for="reaction">Реакция:</label>
      <select id="reaction" v-model="newComment.reaction">
        <option value="-1">Отрицательная</option>
        <option value="0">Нейтральная</option>
        <option value="1">Положительная</option>
      </select>

      <button type="submit" :disabled="isSubmitting">Отправить</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newComment: {
        name: '',
        text: '',
        reaction: '0'
      },
      isSubmitting: false
    };
  },
  methods: {
    submitComment() {
      // Метод для отправки комментария
      this.$emit('comment-added', { ...this.newComment });
      this.resetForm();
    },
    resetForm() {
      // Сброс формы
      this.newComment = {
        name: '',
        text: '',
        reaction: '0'
      };
      this.isSubmitting = false;
    }
  }
};
</script>

<style scoped>
/* Стили для формы */
.comment-form {
  background-color: #fff;
  border-radius: 8px;
  margin-bottom: 20px;
  padding: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

form {
  display: grid;
  gap: 10px;
}

label {
  display: block;
  font-weight: bold;
}

input,
textarea,
select {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
}

button {
  background-color: #4caf50;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 4px;
  cursor: pointer;
}

button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>
