<template>
  <div class="container">
    <Chatbox :chatMessages="chatMessages" />
    <InputGroup @sendMessage="handleSendMessage" />
  </div>
</template>

<script>
import Header from './Header.vue';
import Chatbox from './Chatbox.vue';
import InputGroup from './InputGroup.vue';

export default {
  name: 'Main',
  components: {
    Header,
    Chatbox,
    InputGroup
  },
  data() {
    return {
      chatMessages: []
    };
  },
  methods: {
    async handleSendMessage(message) {
      if (message.trim() !== '') {
        this.chatMessages.push({ sender: '你', message });

        try {
          const response = await fetch(`http://localhost:8080/ai/chat?msg=${encodeURIComponent(message)}`);
          if (!response.ok) {
            throw new Error('Network response was not ok');
          }
          const aiResponse = await response.text();
          this.chatMessages.push({ sender: 'AI', message: aiResponse });
        } catch (error) {
          console.error('Error in AI Response:', error);
          this.chatMessages.push({ sender: 'AI', message: 'AI响应失败' });
        }
      } else {
        console.log('Input is empty');
      }
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vh;
  /* background-color: rgba(255, 255, 255, 0.8); */
  background-color: hsla(186, 44%, 41%, 0.623); 
  padding: 20px;
  border-radius: 40px; /* 添加圆角 */
}
body {
  font-family: Arial, sans-serif;
  background-image: url('data:image/jpeg;base64,');
  background-size: cover;
  background-position: center;
  color: #333;
  margin: 0;
  padding: 0;


}
</style>
