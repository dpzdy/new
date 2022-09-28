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
          text: "Basic Radar Chart",
        },
        legend: {
          data: ["Allocated Budget", "Actual Spending"],
        },
        radar: {
          // shape: 'circle',
          indicator: [
            { name: "Sales", max: 6500 },
            { name: "Administration", max: 16000 },
            { name: "Information Technology", max: 30000 },
            { name: "Customer Support", max: 38000 },
            { name: "Development", max: 52000 },
            { name: "Marketing", max: 25000 },
          ],
        },
        series: [
          {
            name: "Budget vs spending",
            type: "radar",
            data: [
              {
                value: [4200, 3000, 20000, 35000, 50000, 18000],
                name: "Allocated Budget",
              },
              {
                value: [5000, 14000, 28000, 26000, 42000, 21000],
                name: "Actual Spending",
              },
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
