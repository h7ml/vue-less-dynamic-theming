<template>
  <div class="hello">
    <div class="box-1"></div>
    <div class="box-2"></div>
    <p>我是测试文字</p>
    <button @click="defaultTheme">默认主题</button>
    <button @click="dark">暗黑主题</button>
    <button @click="custom">自定义主题</button>
  </div>
</template>


<script>
import { setTheme } from "../theme/theme";
export default {
  name: "HelloWorld",
  mounted() {
    this.init(); // 初始化主题
  },
  methods: {
    init() {
      setTheme("default"); // 初始化未默认主题
    },
    // 更改为默认主题
    defaultTheme() {
      setTheme("default");
    },
    // 更改为暗黑主题
    dark() {
      setTheme("dark");
    },
    // 更改为自定义主题
    custom() {
      let newColor = {
        r: 12,
        g: 33,
        b: 234,
      };
      let newPrimaryColor = `${newColor.r},${newColor.g},${newColor.b}`;
      localStorage.setItem("primaryColor", newPrimaryColor); // 将新的主题色存入本地
      setTheme();
    },
  },
};
</script>
<style scoped lang="less">
.hello {
  display: flex;
  flex-direction: column;
  align-items: center;
  .box-1 {
    width: 50px;
    height: 50px;
    margin-bottom: 30px;
    background: rgba(@primaryColor, 1);
  }
  .box-2 {
    width: 50px;
    height: 50px;
    margin-bottom: 30px;
    background: rgba(@primaryColor, 0.3);
  }
  p {
    color: @primaryTextColor;
  }
}
</style>