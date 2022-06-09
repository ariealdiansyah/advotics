<template>
  <q-card class="no-shadow no-border transparent">
    <q-card-section>
      <div class="row">
        <div class="col-12">
          <q-card class="bg-white q-mt-sm shadow-11">
            <q-card-section>
              <div class="text-h6 text-grey-8 text-weight-bolder">Stack Bar Chart</div>
            </q-card-section>
            <q-card-section class="q-pa-none map_height">
              <IEcharts :option="getStackBarChartOptions" :resizable="true" />
            </q-card-section>
          </q-card>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>
<script>
import IEcharts from 'vue-echarts-v3/src/full.js';

export default {
  name: 'charts',
  data() {
    return {};
  },
  methods: {},
  components: {
    IEcharts,
  },
  computed: {
    getStackBarChartOptions() {
      return {
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'shadow',
          },
        },
        legend: {
          data: ['Gross', 'Nett', 'APV', 'Total'],
          bottom: 20,
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '20%',
          top: '5%',
          containLabel: true,
        },
        xAxis: {
          type: 'category',
          data: ['Dataset 1', 'Dataset 2', 'Dataset 3', 'Dataset 4'],
        },
        yAxis: {
          type: 'value',
        },
        series: [
          {
            name: 'Gross',
            type: 'bar',
            stack: 'ad',
            label: {
              normal: {
                show: true,
                position: 'insideRight',
              },
            },
            data: [32000, 30200, 30100, 33040],
          },
          {
            name: 'Nett',
            type: 'bar',
            stack: 'ad',
            label: {
              normal: {
                show: true,
                position: 'insideRight',
              },
            },
            data: [12000, 13020, 10010, 10304],
          },
          {
            name: 'APV',
            type: 'bar',
            stack: 'ad',
            label: {
              normal: {
                show: true,
                position: 'insideRight',
              },
            },
            data: [22000, 10802, 19001, 20304],
          },
          {
            name: 'Total',
            type: 'line',
            data: [32000, 30200, 30100, 33040],
            emphasis: {
              focus: 'series',
            },
            markLine: {
              lineStyle: {
                type: 'dashed',
              },
              data: [[{ type: 'min' }, { type: 'max' }]],
            },
          },
        ],
      };
    },
  },
};
</script>
<style scoped>
.map_height {
  height: 398px;
}
</style>
