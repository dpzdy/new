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
        tooltip: {
          trigger: "item",
        },
        legend: {
          top: "5%",
          left: "center",
        },
        series: [
          {
            name: "Access From",
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: "40",
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 1048, name: "Search Engine" },
              { value: 735, name: "Direct" },
              { value: 580, name: "Email" },
              { value: 484, name: "Union Ads" },
              { value: 300, name: "Video Ads" },
            ],
          },
        ],
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
