<template>
  <div :style="backgroundStyle" id="app">
    <Header />
    <Main />
    <a-radio-group v-model="selectedValue" @change="radioChange">
      <a-radio-button value="0"> <icon-font type="icon-cucaodu" /> </a-radio-button>
      <a-radio-button value="1"> <icon-font type="icon-iconbeifen3" /> </a-radio-button>
      <a-radio-button value="2"> <icon-font type="icon-duihao_o" /> </a-radio-button>
      <a-radio-button value="3"> <icon-font type="icon-iconbeifen3" /> </a-radio-button>
    </a-radio-group>
    <button @click="nextBackground" id="Button">切换壁纸</button>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

// 预加载图片
import sky1 from '@/images/sky1.png'
import sky2 from '@/images/sky2.png'
import sky3 from '@/images/sky3.png'
import sky4 from '@/images/sky4.png'

export default {
  components: {
    Header,
    Main,
  },
  data() {
    return {
      coverImgUrl: sky1, // 初始背景图片的地址
      selectedValue: 0, // 存储单选按钮的选中值
      backgrounds: [sky1, sky2, sky3, sky4], // 背景图片列表
      currentIndex: 0 // 当前背景图片的索引
    };
  },
  computed: {
    // 计算属性，用于生成背景样式
    backgroundStyle() {
      return {
        backgroundImage: `url(${this.coverImgUrl})`,
      }
    }
  },
  methods: {
    // 切换背景图片的方法
    radioChange(e) {
      let num = parseInt(e.target.value);
      this.coverImgUrl = this.backgrounds[num];
      this.currentIndex = num;
    },
    // 按钮切换背景图片的方法
    nextBackground() {
      this.currentIndex = (this.currentIndex + 1) % this.backgrounds.length;
      this.coverImgUrl = this.backgrounds[this.currentIndex];
      this.selectedValue = this.currentIndex; // 同步单选按钮的选中状态
    }
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  height: 100%;
  width: 100%;
  font-family: 'SimSun', 'FangSong', 'STFangsong';
  background-size: cover;
  background-color: rgb(236, 208, 168);
  background-attachment: fixed;
  background-position: center center;
  position: relative; /* 为了让绝对定位的子元素相对于#app定位 */
}

#Button {
  padding: 10px 15px; /* 增加按钮尺寸 */
  font-size: 1.2em; /* 增大字体 */
  background-color: ghostwhite;
  color: rgb(230, 115, 44);
  border: 4px solid skyblue;
  cursor: pointer;
  transition: all 0.3s ease; /* 添加过渡效果 */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* 添加阴影 */
  border-radius: 5px; /* 添加圆角 */
  position: absolute; /* 绝对定位 */
  right: 20px; /* 距离右边20px */
  bottom: 20px; /* 距离底部20px */
}

/* 悬停效果 */
#Button:hover {
  background-color: rgb(230, 115, 44); /* 悬停时背景颜色变化 */
  color: white; /* 悬停时文字颜色变化 */
  transform: scale(1.05); /* 悬停时放大 */
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.2); /* 悬停时阴影变化 */
}
</style>
