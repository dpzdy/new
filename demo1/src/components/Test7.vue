<template>
  <div class="reveal-bottom">demo</div>
</template>

<script>
import scrollReveal from 'scrollreveal';
export default {
  data() {
    return {
      scrollReveal: scrollReveal(), //页面滚动动画
    };
  },

  mounted() {
    window.addEventListener("scroll", this.scrollArea);

    this.scrollReveal.reveal(".reveal-bottom", {
      // 动画的时长
      duration: 1000,
      // 延迟时间
      delay: 150,
      // 动画开始的位置，'bottom', 'left', 'top', 'right'
      origin: "bottom",
      // 回滚的时候是否再次触发动画
      reset: true,
      // 在移动端是否使用动画
      mobile: true,
      // 滚动的距离，单位可以用%，rem等
      distance: "40px",
      // 其他可用的动画效果
      opacity: 0.001,
      easing: "linear",
      scale: 1,
    });
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.scrollArea);
  },
};
</script>

<style></style>
