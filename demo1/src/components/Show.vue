<template>
  <div>
    <div ref="chart" id="chart"></div>
    <!-- <div ref="chart1" style="width: 50%; height: 376px"></div> -->
  </div>
</template>

<script>
import * as echarts from "echarts";
export default {
  name: "EchartsPie",
  data() {
    return {
      myChart: {},
      option: {
        graphic: {
          elements: [
            {
              type: "text",
              left: "center",
              top: "center",
              style: {
                text: "开 天",
                fontSize: 80,
                fontWeight: "bold",
                lineDash: [0, 200],
                lineDashOffset: 0,
                fill: "transparent",
                stroke: "#000",
                lineWidth: 1,
              },
              keyframeAnimation: {
                duration: 3000,
                loop: true,
                keyframes: [
                  {
                    percent: 0.7,
                    style: {
                      fill: "transparent",
                      lineDashOffset: 200,
                      lineDash: [200, 0],
                    },
                  },
                  {
                    // Stop for a while.
                    percent: 0.8,
                    style: {
                      fill: "transparent",
                    },
                  },
                  {
                    percent: 1,
                    style: {
                      fill: "black",
                    },
                  },
                ],
              },
            },
          ],
        },
      },
    };
  },
  mounted() {
    this.myChart = echarts.init(this.$refs.chart);
    this.update();
  },
  methods: {
    update() {
      // this.option.series.data = this.data
      this.myChart.setOption(this.option);
      window.addEventListener("resize", () => {
        this.myChart.resize();
      });
      this.$on("hook:destroyed", () => {
        window.removeEventListener("resize", function () {
          this.myChart.resize();
        });
      });
    },
  },
};
</script>

<style>
#chart {
  width: 100%;
  height: 50vh;
}
</style>
