<template>
  <div id="test6" class="chartsContainor">
    <div class="pie chart">
      <Pie></Pie>
    </div>
    <div class="bar chart">
      <Bar></Bar>
    </div>
    <div class="line chart">
      <Eline></Eline>
    </div>
    <div class="chart">
      <Wordcloud></Wordcloud>
      <Radar></Radar>
      <Show></Show>
    </div>
    <!-- <p>123</p> -->
  </div>
</template>

<script>
import Pie from "../components/Pie"
import Bar from "../components/Bar"
import Eline from "../components/Eline"
import Wordcloud from "../components/Wordcloud"
import Radar from "./Radar"
import Show from "./Show"
export default {
  components: {
    Pie,
    Bar,
    Eline,
    Wordcloud,
    Radar,
    Show,
  }
}
</script>

<style>
.chartsContainor{
  width: 100%;
  height: 100vh;
}
.chart{
  /* display: inline-block; */
  width: 50%;
  margin: 10px auto; 
  
  /* height: 300px;*/
}
/* .pie{
  position: relative;
  top:10%

} */
</style>