<template>
  <div>
    <div class="box100">0</div>
    <div class="box100">100</div>
    <!--目标元素——页面下滚到该位置，该元素会吸顶-->
    <div class="targetBlock" id="target" :class="{ targetFixed: ifFixed }">
      页面下滚到我这时，我会吸顶哦！（自动悬浮吸附到页面顶部）
    </div>
    <div class="box100">300</div>
    <div class="box100">400</div>
    <div class="box100">500</div>
    <div class="box100">600</div>
    <div class="box100">700</div>
    <div class="box100">800</div>
    <div class="box100">900</div>
    <div class="box100">1000</div>
    <div class="box100">1100</div>
    <div class="box100">1200</div>
    <div class="box100">1000</div>
    <div class="box100">00000</div>
    <div class="box100">00000</div>
    <div class="box100">00000</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      // 是否吸顶
      ifFixed: false,
      // 目标元素与整个文档顶部间的距离
      targetTop: 0,
    };
  },
  mounted() {
    // 监听页面滚动事件
    window.addEventListener("scroll", this.scrolling);
    // 获取目标元素与整个文档顶部间的距离
    this.targetTop = document.querySelector("#target").offsetTop;
  },
  methods: {
    scrolling() {
      // 获取当前滚动条向下滚动的距离
      let scrollTop =
        document.documentElement.scrollTop || document.body.scrollTop;
      if (scrollTop > this.targetTop) {
        this.ifFixed = true;
      } else {
        this.ifFixed = false;
      }
    },
  },
};
</script>
<style scoped>
.targetFixed {
  position: fixed;
  top: 0px;
}

.targetBlock {
  background: red;
  height: 100px;
  border: 1px solid black;
  width: 100%;
}

.box100 {
  height: 100px;
  background: #3a8ee6;
  border: 1px solid black;
}
</style>
