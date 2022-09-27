<template>
  <div class="containor" id="test4">
    <div class="left">
      <img class="leftpic" src="../assets/2.jpg" alt="" />
      <img class="kaipic" src="../assets/3.jpg" alt="" />
      <img class="bottom" src="../assets/moon.png" alt="" />
    </div>
    <div class="right">
      <img class="rightpic" src="../assets/2.jpg" alt="" />
      <img class="tianpic" src="../assets/4.jpg" alt="" />
    </div>
    <!-- <img class="bottom" src="../assets/moon.png" alt="" /> -->
  </div>
</template>

<script></script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}

.containor {
  /* position: relative; */
  width: 100%;
  height: 100vh;
  display: inline-block;
}

.left {
  float: left;
  width: 50%;
  height: 100vh;
  background-color: pink;
  /* display: inline-block; */
}
.right {
  position: relative;
  float: right;
  width: 50%;
  height: 100vh;
  background-color: green;
  /* display: inline-block; */
}
img {
  display: inline;
}
.bottom {
  /* display: ; */
  /* float: left; */
  position: relative;
  top: 17%;
  left: 50%;
  z-index: 2;
  width: 16%;
}
.logo {
  position: relative;
  /* float: left; */
  top: 25%;
  left: 47%;
  z-index: 4;
  width: 6%;
}
.leftpic {
  position: relative;
  top: 20%;
  left: 10%;
  /* float: left; */
  z-index: 3;
  width: 30%;
}
.rightpic {
  position: relative;
  top: 20%;
  right: -60%;
  z-index: 3;
  width: 30%;
}
.kaipic {
  position: relative;
  top: 4%;
  right: -40%;
  z-index: 4;
  width: 12%;
}
.tianpic {
  position: relative;
  top: 20%;
  right: 10%;
  z-index: 4;
  width: 12%;
}
</style>
