<template>
  <div class="charts-overview">
    <h2 class="page-title" style="text-align:center">安全策略</h2>
    <div>
      <b-row>
        <b-col xs="12" lg="3">
          <Widget
            title="<h5>Apex <span class='fw-semi-bold'>Column Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <apexchart
              type="bar"
              height="180"
              :series="cd.apex.column.series"
              :options="cd.apex.column.options"
            />
          </Widget>
        </b-col>
                <b-col xs="12" lg="6">
          <Widget>
            <b-row>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">综合指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
            </b-row>
          </Widget>
        </b-col>
        <b-col xs="12" lg="3">
          <Widget
            title="<h5>Echarts <span class='fw-semi-bold'>Line Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <echart
              :options="cd.echarts.line"
              :init-options="initEchartsOptions"
              style="height: 200px"
            ></echart>
          </Widget>
        </b-col>
        <b-col xs="12" lg="3">
          <Widget
            title="<h5>Highcharts <span class='fw-semi-bold'>Line Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <highcharts :options="cd.highcharts.mixed"></highcharts>
          </Widget>
        </b-col>
        <b-col lg="3">
          <Widget
            title="<h5>Apex <span class='fw-semi-bold'>Monochrome Pie</span></h5>"
            close
            collapse
            customHeader
          >
            <apexchart
              type="pie"
              height="180"
              :series="cd.apex.pie.series"
              :options="cd.apex.pie.options"
            />
          </Widget>
        </b-col>
      </b-row>
      <b-row>
        <b-col xs="12" lg="3">
          <Widget
            title="<h5>Echart <span class='fw-semi-bold'>Donut Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <echart
              :options="cd.echarts.donut"
              :init-options="initEchartsOptions"
              style="height: 175px"
            ></echart>
          </Widget>
        </b-col>
        <b-col xs="12" lg="6">
          <Widget>
            <b-row>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">综合指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
              <b-col col-lg-5ths>
                <h5 style="text-align:center">运行指数</h5>
                <echart
                  :options="cd.echarts.goodpie"
                  :init-options="initEchartsOptions"
                  style="height: 100px; width:100px"
                ></echart>
              </b-col>
            </b-row>
          </Widget>
        </b-col>
        <b-col xs="12" lg="3">
          <Widget
            title="<h5>Highcharts <span class='fw-semi-bold'>Live Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <highcharts :options="ld" ref="highchart"></highcharts>
          </Widget>
        </b-col>

        <b-col xs="12" lg="6">
          <Widget
            title="<h5>Echart <span class='fw-semi-bold'>River Chart</span></h5>"
            close
            collapse
            customHeader
          >
            <echart
              :options="cd.echarts.river"
              :init-options="initEchartsOptions"
              style="height: 350px;"
            ></echart>
          </Widget>
        </b-col>
      </b-row>
    </div>
  </div>
</template>

<script>
import Widget from "@/components/Widget/Widget";
import { chartData, liveChart, liveChartInterval } from "./mock";

import ECharts from "vue-echarts/components/ECharts";
import "echarts/lib/chart/line";
import "echarts/lib/chart/themeRiver";
import "echarts/lib/chart/pie";
import "echarts/lib/component/tooltip";
import "echarts/lib/component/legend";

import Highcharts from "highcharts";
import exporting from "highcharts/modules/exporting";
import exportData from "highcharts/modules/export-data";

exporting(Highcharts);
exportData(Highcharts);

import { Chart } from "highcharts-vue";
import Sparklines from "../../components/Sparklines/Sparklines";

export default {
  name: "Charts",
  components: { Widget, echart: ECharts, highcharts: Chart, Sparklines },
  data() {
    return {
      cd: chartData,
      ld: liveChart,
      initEchartsOptions: {
        renderer: "canvas"
      }
    };
  },
  computed: {
    sparklineData() {
      return {
        series: [{ data: [1, 7, 3, 5, 7, 8] }],
        options1: {
          colors: [this.appConfig.colors.green],
          plotOptions: {
            bar: {
              columnWidth: "50%"
            }
          }
        },
        options2: {
          colors: [this.appConfig.colors.red],
          plotOptions: {
            bar: {
              columnWidth: "50%"
            }
          }
        }
      };
    }
  },
  beforeDestroy() {
    clearInterval(liveChartInterval);
  }
};
</script>
<style src="./Charts.scss" lang="scss" />
