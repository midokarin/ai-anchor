<template>
    <div class="chatbox" ref="chatbox">
      <!-- Chat messages will appear here -->
    </div>
  </template>
  
  <script>
  export default {
    name: 'Chatbox',
    props: ['chatMessages'],
    watch: {
      chatMessages() {
        this.$nextTick(() => {
          const chatbox = this.$refs.chatbox;
          chatbox.scrollTop = chatbox.scrollHeight;
        });
      }
    }
  };
  </script>
  
  <style scoped>
  .chatbox {
    background: rgba(165, 201, 209, 0.7); /* 半透明背景 */
    background-size: auto;
    width: 100%;
    max-width: 800px;
    height: 600px;
    border: 2px solid #ccc;
    padding: 10px;
    margin-top: 20px;
    overflow-y: scroll;
    border-radius: 10px; /* 添加圆角 */
  }
  </style>
  