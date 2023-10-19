<template>
  <div class="comment" :style="{ backgroundColor: getBackgroundColor() }">
    <div class="comment-header">
      <strong>{{ comment.name }}</strong> - {{ formatDate(comment.timestamp) }}
    </div>
    <div class="comment-body">
      {{ comment.text }}
    </div>
    <div class="comment-reaction">
      <span v-if="comment.reaction === -1">Отрицательная реакция</span>
      <span v-else-if="comment.reaction === 0">Нейтральная реакция</span>
      <span v-else>Положительная реакция</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['comment'],
  methods: {
    getBackgroundColor() {
      const reaction = parseInt(this.comment.reaction, 10);
      switch (reaction) {
        case -1:
          return '#ffcdd2';  //Крачный
        case 0:
          return '#fff';  //Белы
        case 1:
          return '#c8e6c9';    // Зеленый
        default:
          return '#fff';
      }
    },
    formatDate(timestamp) {
      const date = new Date(timestamp);
      return date.toLocaleString();
    }
  }
};
</script>

<style scoped>
.comment {
  background-color: #fff;
  border-radius: 8px;
  margin-bottom: 20px;
  padding: 15px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.comment-header {
  font-weight: bold;
  margin-bottom: 10px;
}

.comment-reaction {
  margin-top: 10px;
  font-style: italic;
}

.comment-reaction span {
  display: inline-block;
  margin-right: 10px;
}

</style>
