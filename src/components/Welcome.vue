<template>
    <div>
        <el-row :gutter="12">
        <el-col :span="5" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span style="color: #A7A09B; font-size: 15px;">用户访问统计</span>
            </div>
            <div class="text item" style="text-align:center; font-size:30px;">
            <b>
                612
            </b>
            </div>
            </el-card>
        </el-col>
        <el-col :span="5" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span style="color: #A7A09B; font-size: 15px">用户登录统计</span>
            </div>
            <div class="text item" style="text-align:center; font-size:30px">
            <b>
                604
            </b>
            </div>
            </el-card>
        </el-col>
        <el-col :span="5" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span style="color: #A7A09B; font-size: 15px">服务产品总数（已发布）</span>
            </div>
            <div class="text item" style="text-align:center; font-size:30px">
            <b>
                55
            </b>
            </div>
            </el-card>
        </el-col>
        <el-col :span="4" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span style="color: #A7A09B; font-size: 15px">产品组（已发布）</span>
            </div>
            <div class="text item" style="text-align:center; font-size:30px">
            <b>
                7
            </b>
            </div>
            </el-card>
        </el-col>
        <el-col :span="5" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span style="color: #A7A09B; font-size: 15px">注册用户</span>
            </div>
            <div class="text item" style="text-align:center; font-size:30px">
            <b>
                4247
            </b>
            </div>
            </el-card>
        </el-col>
        </el-row>
        <el-row :gutter="12">
        <el-col :span="15" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span><b>产品管理员业务流总览</b></span>
            </div>
            <div class="text item" style="height: 50px;">
                604
            </div>
            </el-card>
        </el-col>
        <el-col :span="9" style="padding: 20px 5px;">
            <el-card class="box-card">
            <div slot="header">
                <span><b>快捷入口</b></span>
            </div>
            <div class="text item">
                <el-row style="height: 50px;">
                <el-button round style="background-color: #108C76; color: #fff; font-size: 10px; position: absolute; left: 50px; width: 18%; margin: 10px;">产品发布</el-button>
                <el-button round style="background-color: #108C76; color: #fff; font-size: 10px; position: absolute; left: 270px; width: 18%; margin: 10px;">数据发布</el-button>
                <el-button round style="background-color: #108C76; color: #fff; font-size: 10px; position: absolute; left: 490px; width: 18%; margin: 10px;">农情反馈</el-button>
                </el-row>
            </div>
            </el-card>
        </el-col>
        </el-row>
        <el-row :gutter="12">
        <el-col :span="15" style="padding: 20px 5px;">
            <el-card class="box-card">
                <div slot="header">
                    <span><b>各栏目业务产品发布统计</b></span>
                </div>
                <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
                <div id="main" style="width: 100%; height: 320px; padding: 0px;">
                </div>
            </el-card>
        </el-col>
        <el-col :span="9" style="padding: 20px 5px;">
            <el-card class="box-card">
                <div slot="header">
                    <span><b>注册用户分布情况</b></span>
                </div>
                <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
                <div id="main_02" style="height:320px;">
                </div>
            </el-card>
        </el-col>
        </el-row>
    </div>
</template>

<script>
import * as echarts from 'echarts'
// 导入echarts
export default {
  data () {
    return {}
  },
  created () {},
  // 此时页面上的元素，已经被渲染完毕
  mounted () {
    // 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById('main'))

    // 准备数据和配置项
    var option = {
      tooltip: {},
      xAxis: {
        data: ['气象预警', ' ', '天气快报', ' ', '气象科普', ' ', '农业预报', ' ', '测试栏目01', ' ', '种植管理技术', ' ', '测试栏目02']
      },
      yAxis: {},
      series: [{
        name: '销量',
        type: 'bar',
        data: [5, 2, 2, 4, 1, 2, 8, 1, 1, 9, 1, 10, 10]
      }]
    }
    // 展示数据
    myChart.setOption(option)
  },
  methods: {}
}
</script>

<style Lang="less" scoped>
</style>
