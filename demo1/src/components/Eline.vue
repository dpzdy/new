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
        title: {
          text: "Stacked Line",
        },
        tooltip: {
          trigger: "axis",
        },
        legend: {
          data: ["Email", "Union Ads", "Video Ads", "Direct", "Search Engine"],
        },
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          containLabel: true,
        },
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
        },
        series: [
          {
            name: "Email",
            type: "line",
            stack: "Total",
            data: [120, 132, 101, 134, 90, 230, 210],
          },
          {
            name: "Union Ads",
            type: "line",
            stack: "Total",
            data: [220, 182, 191, 234, 290, 330, 310],
          },
          {
            name: "Video Ads",
            type: "line",
            stack: "Total",
            data: [150, 232, 201, 154, 190, 330, 410],
          },
          {
            name: "Direct",
            type: "line",
            stack: "Total",
            data: [320, 332, 301, 334, 390, 330, 320],
          },
          {
            name: "Search Engine",
            type: "line",
            stack: "Total",
            data: [820, 932, 901, 934, 1290, 1330, 1320],
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
