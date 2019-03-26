<template>
  <div id="main" ref="edata" style="width: 600px;height:400px;"></div>
</template>

   
<script>

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      // 基本使用
      // option: {
      //   title: {
      //     text: 'ECharts 入门示例'
      //   },
      //   tooltip: {},
      //   legend: {
      //     data: ['销量']
      //   },
      //   xAxis: {
      //     data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
      //   },
      //   yAxis: {},
      //   series: [{
      //     name: '销量',
      //     type: 'bar',
      //     data: [5, 20, 36, 10, 10, 20]
      //   }]
      // }
      // option: {
      //   title: { //标题
      //     x: 'center',
      //     y: 5,
      //     text: '数量和占比图'    //换行用 \n
      //   },
      //   legend: { //图标
      //     show: true,
      //     x: 'center',
      //     y: 30,
      //     itemGap: 10,
      //     itemWidth: 30,
      //     itemHeight: 10,
      //     data: ['one', 'three']
      //   },
      //   color: ['#3398DB'],//  柱状图颜色

      //   tooltip: { //鼠标悬停提示内容
      //     trigger: 'axis',
      //     axisPointer: {            // 坐标轴指示器，坐标轴触发有效
      //       type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
      //     }
      //   },
      //   grid: { //布局   控制图的大小，调整下面这些值就可以
      //     left: '3%',
      //     right: '4%',
      //     bottom: '3%',
      //     containLabel: true
      //     //y2 : 40
      //     // y2可以控制 X轴跟Zoom控件之间的间隔，避免以为倾斜后造成 label重叠到zoom上
      //   },
      //   xAxis: [ //X轴
      //     {
      //       type: 'category',
      //       data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      //       axisTick: {
      //         alignWithLabel: true
      //       }
      //     }
      //   ],
      //   yAxis: [ //两个y轴
      //     {
      //       type: 'value',
      //       axisLabel: {
      //         show: true,
      //         interval: 'auto',
      //         formatter: '{value} '
      //       },
      //       splitNumber: 10,
      //       splitLine: {
      //         show: true,
      //         lineStyle: {
      //           type: 'dashed'
      //         }
      //       },
      //       splitArea: {
      //         show: false
      //       }
      //     },
      //     {
      //       type: 'value',
      //       axisLabel: {
      //         show: true,
      //         interval: 'auto',
      //         formatter: '{value} %'
      //       },
      //       splitNumber: 10,
      //       splitLine: {
      //         show: true,
      //         lineStyle: {
      //           type: 'dashed'
      //         }
      //       },
      //       splitArea: {
      //         show: false
      //       }
      //     }
      //   ],
      //   series: [ //用于指定图标显示类型

      //     {
      //       name: 'one',
      //       type: 'bar',
      //       barMaxWidth: 100,
      //       yAxisIndex: '0',//使用第一个y轴
      //       itemStyle: {
      //         normal: {
      //           color: 'rgba(139,26,26,1)',  //柱子颜色
      //           borderType: 'dashed',

      //           label: { //设置柱子上面的内容
      //             show: false, //数据是否显示在柱子上
      //             position: 'inside',
      //             offset: [0, 0],
      //             formatter: '{c}',  //如果是百分比：formatter : '{c}%',
      //             textStyle: {//字体内容设置
      //               color: '#000000',
      //               fontStyle: 'normal',
      //               fontWeight: 'normal',
      //               fontFamily: 'sans-serif',
      //               fontSize: 6
      //             }
      //           }
      //         }
      //       },
      //       data: [10, 52, 200, 334, 390, 330, 220]
      //     },
      //     {
      //       name: 'percent',
      //       type: 'line',
      //       symbol: 'emptyCircle',
      //       showAllSymbol: true, //动画效果
      //       symbolSize: 12,
      //       smooth: true, //光滑的曲线
      //       // yAxisIndex: '1',
      //       itemStyle: {
      //         normal: {
      //           color: 'rgba(139,26,26,1)',
      //           label: {
      //             show: true,
      //             formatter: '{c}%',
      //             textStyle: {
      //               color: '#000000'
      //             }
      //           }
      //         }
      //       },
      //       data: [1, 5, 20, 33, 39, 33, 22]

      //     },
      //   ]
      // }


      option: {
        tooltip: {
          trigger: 'axis',
          axisPointer: {            // 坐标轴指示器，坐标轴触发有效
            type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
          },
          formatter: function (params) { //自定义函数修改折线图给数据加单位
            console.log(params)
            var str = '';//声明一个变量用来存储数据
            str += '<div>' + params[0].name + '</div>';   //显示日期的函数
            for (var i = 0; i < params.length; i++) {  //图显示的数据较多时需要循环数据，这样才可以成功的给多条数据添加单位
              str += '<span style="display:inline-block;margin-right:5px;border-radius:10px;width:10px;height:10px;background-color:' + params[i].color + ';"></span>' + params[i].seriesName + '</span> : <span>' + (params[i].data ? params[i].data + '%' : '暂无') + '</br>';
            }



            
            return str;
          }
        },
        legend: {
          data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎', '百度', '谷歌', '必应', '其他']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            type: 'category',
            data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日']
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '直接访问',
            type: 'bar',
            data: [320, 332, 301, 334, 390, 330, 320]
          },
          {
            name: '邮件营销',
            type: 'bar',
            stack: '广告',
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: '联盟广告',
            type: 'bar',
            stack: '广告',
            data: [220, 182, 191, 234, 290, 330, 310]
          },
          {
            name: '视频广告',
            type: 'bar',
            stack: '广告',
            data: [150, 232, 201, 154, 190, 330, 410]
          },
          {
            name: '搜索引擎',
            type: 'bar',
            data: [862, 1018, 964, 1026, 1679, 1600, 1570],
            markLine: {
              lineStyle: {
                normal: {
                  type: 'dashed'
                }
              },
              data: [
                [{ type: 'min' }, { type: 'max' }]
              ]
            }
          },
          {
            name: '百度',
            type: 'bar',
            barWidth: 5,
            stack: '搜索引擎',
            data: [620, 732, 701, 734, 1090, 1130, 1120]
          },
          {
            name: '谷歌',
            type: 'bar',
            stack: '搜索引擎',
            data: [120, 132, 101, 134, 290, 230, 220]
          },
          {
            name: '必应',
            type: 'bar',
            stack: '搜索引擎',
            data: [60, 72, 71, 74, 190, 130, 110]
          },
          {
            name: '其他',
            type: 'bar',
            stack: '搜索引擎',
            data: [62, 82, 91, 84, 109, 110, 120]
          }
        ]
      }
    }
  },
  // var myChart = echarts.init(document.getElementById('main'));
  mounted() {
    // let myChart = echarts.init(this.$refs.edata)
    this.drawCharts();
    // myChart.setOption(this.option);

  },
  methods: {
    drawCharts() {
      // var myChart = this.echarts.init(document.getElementById('main'));
      let myChart = this.echarts.init(this.$refs.edata)

      myChart.setOption(this.option);
    }

  },


}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
