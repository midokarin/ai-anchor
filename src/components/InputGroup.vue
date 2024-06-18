<template>
  <div class="input-group">
    <input type="text" v-model="userInput" placeholder="输入你的消息..." @keyup.enter="sendMessage">
    <button @click="sendMessage">发送</button>
  </div>
</template>

<script>
export default {
  name: 'InputGroup',
  data() {
    return {
      userInput: ''
    };
  },
  methods: {
    sendMessage() {
      this.$emit('sendMessage', this.userInput);
      this.userInput = '';
    }
  }
};
</script>

<style scoped>
.input-group {
  display: flex;
  margin-top: 10px;
}

.input-group input {
  flex: 1;
  padding: 15px 20px; /* 增加内边距 */
  font-size: 1.2em; /* 增大字体 */
  border: 2px solid skyblue; /* 边框颜色 */
  border-radius: 5px; /* 圆角边框 */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* 添加阴影 */
  transition: all 0.3s ease; /* 添加过渡效果 */
  width: 550px; /* 增加输入框长度 */
}

.input-group input:focus {
  border-color: rgb(230, 115, 44); /* 聚焦时边框颜色变化 */
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.2); /* 聚焦时阴影变化 */
  outline: none; /* 去掉默认的聚焦边框 */
}

.input-group button {
  padding: 10px 20px; /* 增加按钮尺寸 */
  font-size: 1.2em; /* 增大字体 */
  background-color: ghostwhite;
  color: rgb(230, 115, 44);
  border: 4px solid skyblue;
  cursor: pointer;
  transition: all 0.3s ease; /* 添加过渡效果 */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* 添加阴影 */
  border-radius: 5px; /* 添加圆角 */
  margin-left: 10px; /* 按钮与输入框之间的间距 */
}

/* 悬停效果 */
.input-group button:hover {
  background-color: rgb(230, 115, 44); /* 悬停时背景颜色变化 */
  color: white; /* 悬停时文字颜色变化 */
  transform: scale(1.05); /* 悬停时放大 */
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.2); /* 悬停时阴影变化 */
}
</style>
