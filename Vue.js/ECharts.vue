<template>
  <div>
    <chart id="chart" :options="chartOption"></chart>
  </div>
</template>

<script>
import Echarts from "vue-echarts";
import "echarts/lib/chart/line";
import "echarts/lib/component/tooltip";
import "echarts/lib/component/axis";
import "echarts/lib/component/dataZoom";
import "echarts/lib/component/markLine";

export default {
  components: { chart: Echarts },
  data() {
    return {
      xData: [1, 2, 3, 4, 5],
      yData: [1, 2, 3, 4, 5],
      startPercent: 0,
      maxYAxis: 0,
      chartOption: {}
    };
  },
  methods: {
    setChartData: function() {
      this.xData = [];
      this.yData = [];
      /* x축 y축 데이터 삽입
      for (var i = 0; i < length; i++) {
        this.xData.push();
        this.yData.push();
      }
      */
    },
    setChartOption: function() {
      const Chart = this;
      this.chartOption = {
        tooltip: {
          trigger: "axis",
          position: function(pt) {
            return [pt[0], "10%"];
          },
          formatter: function(params) {
            // Tooltip 내용
            return "Tooltip";
          },
          // Tooltip Style
          textStyle: {
            fontSize: 16,
            fontWeight: "lighter"
          }
        },
        // 축 값 Style
        axisLabel: {
          color: "#f7f7f7",
          fontWeight: "lighter"
        },
        // X축
        xAxis: {
          type: "category",
          boundaryGap: false,
          data: this.xData
        },
        // Y축
        yAxis: {
          type: "value",
          /* 최대 최소 지정하거나 아래 boundaryGap 지정
          max: this.maxYAxis,
          min: 0,
          */
          boundaryGap: [0, "10%"],
          // 축 값 형식 지정
          axisLabel: {
            formatter: "{value}초"
          }
        },
        dataZoom: [
          {
            type: "inside",
            // 확대bar 시작 %
            start: this.startPercent,
            // 확대bar 끝 %
            end: 100
          },
          // 확대bar Style
          {
            backgroundColor: "rgba(0,0,0,0.2)",
            fillerColor: "rgba(255, 255, 255, 0.8)",
            handleSize: "100%",
            handleStyle: {
              color: "rgb(255,255,255)"
            },
            textStyle: {
              color: "white",
              fontSize: 13,
              fontWeight: "lighter"
            }
          }
        ],
        series: [
          {
            name: "응답시간 ",
            type: "line",
            smooth: false,
            symbol: "circle",
            data: this.yData,
            // 임의의 선 지정
            markLine: {
              data: [
                {
                  // y값 설정
                  yAxis: 3,
                  label: {
                    color: "#ff5b5b",
                    formatter: "Y markLine",
                    textStyle: { fontSize: 16 }
                  },
                  lineStyle: {
                    color: "#ff5b5b",
                    type: "solid",
                    width: 3
                  }
                },
                {
                  // x값 설정
                  xAxis: 3,
                  label: {
                    color: "rgba(0, 187, 153)",
                    formatter: "X markLine",
                    textStyle: { fontSize: 16 }
                  },
                  lineStyle: {
                    color: "rgba(0, 187, 153)",
                    type: "solid",
                    width: 3
                  }
                }
              ]
            },
            // 선 그래프 Style
            itemStyle: {
              color: "lightgray"
            },
            // 영역 Style
            areaStyle: {
              color: new Echarts.graphic.LinearGradient(0, 0, 0, 1, [
                {
                  offset: 0,
                  color: "#ff5b5b" // 영역 끝 색
                },
                {
                  offset: 1,
                  color: "rgba(130,250,150,0.5)" // 영역 시작 색
                }
              ])
            }
          }
        ]
      };
    }
  },
  created() {
    // this.xData, this.yData가 설정된 후 그려져야됨. 구현할땐 watch xData로 구현
    setTimeout(() => {
      this.setChartOption();
    }, 1000);
  }
};
</script>
 
<style>
#chart {
  width: 100%;
}
/* 라이브러리를 감싸고있는 div와 내부의 크기를 동일하게 하기 위해 설정 */
.echarts div {
  overflow: unset !important;
}
</style>