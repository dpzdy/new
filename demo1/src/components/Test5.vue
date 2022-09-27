<template>
  <div class="bgcontainor">
    <canvas id="space"></canvas>
    <img class="kaipic" src="../assets/kai1.png" alt="">
    <img class="tianpic" src="../assets/tian1.png" alt="">

    <img class="leftpic" src="../assets/ren.png" alt="">
    <img class="rightpic" src="../assets/hang.png" alt="">
    <img class="starpic" src="../assets/star.png" @click="go()" alt="">


  </div>
</template>

<script>
export default {
  methods: {
    go(){
      document.getElementById("test4").scrollIntoView({ behavior: 'smooth' });
    },
    init() {
      window.requestAnimFrame = (function () {
        return window.requestAnimationFrame;
      })();
      var canvas = document.getElementById("space");
      var c = canvas.getContext("2d");

      var numStars = 1900;
      var radius = "0." + Math.floor(Math.random() * 9) + 1;
      var focalLength = canvas.width * 2;
      var warp = 0;
      var centerX, centerY;

      var stars = [],
        star;
      var i;

      var animate = true;

      initializeStars();

      function executeFrame() {
        if (animate) requestAnimFrame(executeFrame);
        moveStars();
        drawStars();
      }

      function initializeStars() {
        centerX = canvas.width / 2;
        centerY = canvas.height / 2;

        stars = [];
        for (i = 0; i < numStars; i++) {
          star = {
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height,
            z: Math.random() * canvas.width,
            o: "0." + Math.floor(Math.random() * 99) + 1,
          };
          stars.push(star);
        }
      }

      function moveStars() {
        for (i = 0; i < numStars; i++) {
          star = stars[i];
          star.z--;

          if (star.z <= 0) {
            star.z = canvas.width;
          }
        }
      }

      function drawStars() {
        var pixelX, pixelY, pixelRadius;

        // Resize to the screen
        if (
          canvas.width != window.innerWidth ||
          canvas.width != window.innerWidth
        ) {
          canvas.width = window.innerWidth;
          canvas.height = window.innerHeight;
          initializeStars();
        }
        if (warp == 0) {
          c.fillStyle = "rgba(0,10,20,1)";
          c.fillRect(0, 0, canvas.width, canvas.height);
        }
        c.fillStyle = "rgba(209, 255, 255, " + radius + ")";
        for (i = 0; i < numStars; i++) {
          star = stars[i];

          pixelX = (star.x - centerX) * (focalLength / star.z);
          pixelX += centerX;
          pixelY = (star.y - centerY) * (focalLength / star.z);
          pixelY += centerY;
          pixelRadius = 1 * (focalLength / star.z);

          c.fillRect(pixelX, pixelY, pixelRadius, pixelRadius);
          c.fillStyle = "rgba(209, 255, 255, " + star.o + ")";
          //c.fill();
        }
      }

      executeFrame();
    },
  },
  mounted() {
    this.init();
  },
};
</script>

<style>
.bgcontainor{
  width: 100%;
  height: 100vh;
}
#space {
  width: 100%;
  height: 100vh;
}
.kaipic{
  position: absolute;
  top: 13%;
  right: 45%;
  z-index: 4;
  width: 30%;
}
.tianpic{
  position: absolute;
  top: 33%;
  right: 21%;
  z-index: 4;
  width: 30%;
}

.leftpic{
  position: absolute;
  top: 0%;
  left: 5%;
  z-index: 3;
  width: 38%;
}
.rightpic{
  opacity: 0.6;
  position: absolute;
  top: -15%;
  right: 11%;
  z-index: 3;
  width: 31%;
}
.starpic{
  position: absolute;
  top: 35%;
  right: 43%;
  z-index: 10;
  width: 9%;

}
</style>

