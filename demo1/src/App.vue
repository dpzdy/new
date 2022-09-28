<template>
  <div id="app">
    <!-- <Test1></Test1> -->
    <!-- <Test1></Test1> -->
    <!-- <Test1></Test1> -->
    <!-- <Test2></Test2> -->
    <!-- <Test3></Test3> -->
    <!-- <Test4></Test4> -->
    <!-- <Test5></Test5> -->
    <!-- <Test6></Test6> -->
    <Test7></Test7>

  </div>
</template>

<script>
import Test1 from './components/Test1'
import Test2 from './components/Test2'
import Test3 from './components/Test3'
import Test4 from './components/Test4'
import Test5 from './components/Test5'
import Test6 from './components/Test6'
import Test7 from './components/Test7'



export default {
  name: 'App',
  components: {
    Test1,
    Test2,
    Test3,
    Test4,
    Test5,
    Test6,
    Test7,
  }
}
</script>

<style lang="less">
*{
  padding: 0;
  margin: 0;
  ::-webkit-scrollbar {
    /*隐藏滚轮*/
    display: none;
  }
}

</style>
