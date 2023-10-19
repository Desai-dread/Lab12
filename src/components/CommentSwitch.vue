<!-- src/components/CommentSwitch.vue -->

<template>
  <div class="comment-switch">
    <div class="comment-switch">
      <label>
        <input type="checkbox" v-model="realTimeMode" @change="toggleRealTime">
        Получать комментарии в реальном времени(не работает)
      </label>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // Данные переключателя
      realTimeMode: false // Изначально отключено
    };
  },
  methods: {
    toggleRealTime() {
      // Метод для переключения режима реального времени
      if (this.realTimeMode) {
        // Включено
        console.log('Режим реального времени включен');
      } else {
        // Не знаю
        console.log('Режим реального времени выключен');
      }
    }
  }
};
</script>

<style scoped>

.comment-switch {
  text-align: center;
  margin-bottom: 20px;
}

label {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}

input[type="checkbox"] {
  margin-right: 5px;
  vertical-align: middle;
}
</style>
