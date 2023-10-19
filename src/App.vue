// src/App.vue

<template>
  <div id="app">
    <CommentSwitch />
    <CommentForm @comment-added="addComment" />
    <CommentItem v-for="comment in comments" :key="comment.id" :comment="comment" />
  </div>
</template>

<script>
import CommentItem from './components/CommentItem.vue';
import CommentForm from './components/CommentForm.vue';
import CommentSwitch from './components/CommentSwitch.vue';

export default {
  data() {
    return {
      comments: [
        {
          id: 1,
          name: 'Максон',
          text: 'куда идти, че делать то',
          reaction: 1,
          timestamp: Date.now(),
          replies: []
        },
        {
          id: 2,
          name: 'Лёха',
          text: 'Не согласен',
          reaction: -1,
          timestamp: Date.now() - 1000,
          replies: []
        }
      ]
    };
  },
  methods: {
    addComment(newComment) {
      // Метод для добавления комментария
      newComment.id = this.comments.length + 1;
      newComment.timestamp = Date.now();
      newComment.replies = [];
      this.comments.push(newComment);
    }
  },
  components: {
    CommentItem,
    CommentForm,
    CommentSwitch
  }
};
</script>

<style>
/* Глобальные стили */
@import './styles.css'; /* Ругается */
</style>
