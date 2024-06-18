<template>
  <div class="content">
    <h1>欢迎来到我的个人网页</h1>
    <div v-if="!submitted">
      <form @submit.prevent="handleSubmit">
        <div>
          <label for="name">名字：</label>
          <input type="text" id="name" v-model="name" required>
        </div>
        <div>
          <label for="hobby">爱好：</label>
          <input type="text" id="hobby" v-model="hobby" required>
        </div>
        <button type="submit">提交</button>
      </form>
    </div>
    <div v-else>
      <p>名字：<span id="name">{{ name }}</span></p>
      <p>爱好：<span id="hobby">{{ hobby }}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      name: '',
      hobby: '',
      submitted: false
    };
  },
  methods: {
    handleSubmit() {
      this.submitted = true;
    }
  }
};
</script>

<style scoped>
.content {
  max-width: 600px;
  text-align: center;
  margin: auto; /* 使内容居中 */
  padding: 20px;
  background: rgba(255, 255, 255, 0.8); /* 半透明背景 */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* 添加阴影 */
  animation: fadeIn 2s ease-in-out; /* 淡入动画 */
  border-radius: 10px; /* 添加圆角 */
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

h1 {
  color: lightcoral;
  text-shadow: 4px 4px 8px lightblue;
  font-size: 3.5em;
  margin-bottom: 0.5em;
  animation: glow 1.5s infinite alternate; /* 添加光晕动画 */
}

@keyframes glow {
  from {
    text-shadow: 4px 4px 8px lightblue, 0 0 10px lightblue, 0 0 20px lightblue, 0 0 40px lightblue;
  }
  to {
    text-shadow: 4px 4px 8px lightblue, 0 0 20px lightblue, 0 0 30px lightblue, 0 0 50px lightblue;
  }
}

form {
  margin-top: 20px;
}

label {
  display: block;
  margin: 10px 0 5px;
}

input {
  padding: 10px;
  font-size: 1em;
  width: calc(100% - 22px); /* 考虑 padding 和边框的宽度 */
  margin-bottom: 15px;
  border: 2px solid lightcoral;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

input:focus {
  border-color: lightblue;
  outline: none;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

button {
  padding: 10px 20px;
  font-size: 1em;
  background-color: lightcoral;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: darksalmon;
}

p {
  font-size: 1.2em;
  color: #333;
  margin: 0.5em 0;
}

#name, #hobby {
  font-weight: bold;
  color: #555;
  text-shadow: 2px 2px 4px lightblue;
}
</style>
