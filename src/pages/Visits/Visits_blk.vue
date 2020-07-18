<template>
  <div class="visits-page">
    <h2 class="page-title" style="text-align:center">网络态势总览</h2>
    <b-row>
      <b-col lg="3" xs="12">
        <Widget close collapse customHeader >
          <!-- <highcharts :options="ld" ref="highchart"></highcharts> -->
          <div style="height:100px"></div>
        </Widget>
        <Widget>
          <!-- <highcharts :options="ld" ref="highchart"></highcharts> -->
          <div style="height:100px"></div>
        </Widget>
      </b-col>
      <b-col lg="6">

        <Widget
          title="<h6><span class='badge badge-danger'>全区域</span> 网络资源及运行态势地图</h6>"
          refresh
          close
          customHeader
        >
          <div >
             <highcharts :options="cd.highcharts.piedata" ref="highchart"></highcharts>
            </div><br>
          <Map />
        </Widget>
      </b-col>
      <b-col lg="3" xs="12">
        <Widget>
          <!-- <highcharts :options="ld" ref="highchart"></highcharts> -->
          <div style="height:200px"></div>
        </Widget>
        <Widget>
          <!-- <highcharts :options="ld" ref="highchart"></highcharts> -->
          <div style="height:200px"></div>
        </Widget>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import Vue from "vue";
import Widget from "@/components/Widget/Widget";
import Map from "./components/Map/Map";
import Calendar from "./components/Calendar/Calendar";
import AreaChart from "./components/AreaChart/AreaChart";
import AnimatedNumber from "animated-number-vue";

//The following are for HightCharts
import { chartData, liveChart, liveChartInterval } from "./mock";
import Highcharts from "highcharts";
import exporting from "highcharts/modules/exporting";
import exportData from "highcharts/modules/export-data";
exporting(Highcharts);
exportData(Highcharts);
import { Chart } from "highcharts-vue";

export default {
  name: "Visits_blk",
  components: {
    Widget,
    Map,
    Calendar,
    AreaChart,
    highcharts: Chart,
    AnimatedNumber
  },
  data() {
    return {
      animateNumberOptions: {
        duration: 2000,
        easing: "easeInQuad",
        formatValue(value) {
          return value.toFixed(0);
        }
      },
      checkedArr: [false, false, false],
      dataCollection: null,
      cd: chartData,
      ld: liveChart
    };
  },
  methods: {
    checkTable(id) {
      let arr = [];
      if (id === 0) {
        const val = !this.checkedArr[0];
        for (let i = 0; i < this.checkedArr.length; i += 1) {
          arr[i] = val;
        }
      } else {
        arr = this.checkedArr;
        arr[id] = !arr[id];
      }
      if (arr[0]) {
        let count = 1;
        for (let i = 1; i < arr.length; i += 1) {
          if (arr[i]) {
            count += 1;
          }
        }
        if (count !== arr.length) {
          arr[0] = !arr[0];
        }
      }
      Vue.set(this, "checkedArr", arr);
    },
    fillData() {
      this.dataCollection = {
        labels: [
          this.getRandomInt(),
          this.getRandomInt(),
          this.getRandomInt(),
          this.getRandomInt(),
          this.getRandomInt(),
          this.getRandomInt(),
          this.getRandomInt()
        ],
        datasets: [
          {
            label: "Data One",
            backgroundColor: "#1870DC",
            borderColor: "transparent",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt()
            ]
          },
          {
            label: "Data Two",
            backgroundColor: "#F45722",
            borderColor: "transparent",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt()
            ]
          }
        ]
      };
    },
    getRandomInt() {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5;
    }
  },
  mounted() {
    this.fillData();
  },
  beforeDestroy() {
    clearInterval(liveChartInterval);
  }
};
</script>

<style src="./Visits.scss" lang="scss" />
