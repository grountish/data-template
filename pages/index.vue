<template>
  <div class="pt-20">
    <div class="border shadow py-10 w-11/12 m-auto">
      <h1 class="text-4xl text-center font-extrabold">PIE CHARTS</h1>
      <div class="my-10 z-10">
        <D3PieChart
          :config="chart_config"
          :datum="allData[yearPie]"
        ></D3PieChart>
      </div>

      <div class="grid grid-cols-3 w-50 m-auto">
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearPie--"
        >
          ⇦
        </button>
        <h4 class="m-auto">YEAR : {{ returnYear(yearsPie, yearPie) }}</h4>
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearPie++"
        >
          ⇨
        </button>
      </div>
    </div>
    <div class="border shadow py-10 w-11/12 m-auto">
      <h1 class="text-4xl text-center font-extrabold">LINE CHARTS</h1>
      <div class="my-10 z-10">
        <D3LineChart
          :config="chart_configLine"
          :datum="chart_dataLine[yearLine]"
        ></D3LineChart>
      </div>
      <div class="grid grid-cols-3 w-50 m-auto">
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearLine--"
        >
          ⇦
        </button>
        <h4 class="m-auto">YEAR :{{ returnYear(yearsLine, yearLine) }}</h4>
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearLine++"
        >
          ⇨
        </button>
      </div>
    </div>
    <div class="border shadow py-10 w-11/12 m-auto">
      <h1 class="text-4xl text-center font-extrabold">Bar CHARTS</h1>
      <div class="my-10 z-10">
        <D3BarChart
          :config="chart_configBar"
          :datum="chart_dataBar[yearBar]"
        ></D3BarChart>
      </div>
      <div class="grid grid-cols-3 w-50 m-auto">
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearBar--"
        >
          ⇦
        </button>
        <h4 class="m-auto">YEAR :{{ returnYear(yearsBar, yearBar) }}</h4>
        <button
          class="border border-solid p-4 w-auto m-auto"
          @click="yearBar++"
        >
          ⇨
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { D3PieChart } from 'vue-d3-charts'
import { D3LineChart } from 'vue-d3-charts'
import { D3BarChart } from 'vue-d3-charts'

export default {
  components: {
    D3PieChart,
    D3LineChart,
    D3BarChart,
  },

  data() {
    return {
      yearPie: 0,
      yearLine: 0,
      yearBar: 0,
      yearsPie: ['1920', '1234', '1553'],
      yearsLine: ['2000', '1000'],
      yearsBar: ['1889', '1876', '1895'],
      chart_config: {
        key: 'name',
        value: 'hours',
        color: { scheme: 'schemeTableau10' },
        radius: { inner: 80 },
      },
      value: false,
      color: {
        key: false,
        keys: false,
        scheme: false,
        current: '#1f77b4',
        default: '#AAA',
        axis: '#000',
      },
      currentKey: false,
      margin: {
        top: 20,
        right: 20,
        bottom: 20,
        left: 20,
      },
      transition: {
        duration: 350,
        ease: 'easeLinear',
      },

      allData: [
        [
          { hours: 30, name: 'as' },
          { hours: 10, name: 'Ipsum' },
          { hours: 7, name: 'asdfg' },
          { hours: 5, name: 'Sit' },
        ],
        [
          { hours: 60, name: 'asasdasd' },
          { hours: 1, name: 'asdasdasdasd' },
          { hours: 12, name: 'asASSADDdfg' },
          { hours: 53, name: 'SASit' },
        ],
        [
          { hours: 6, name: 'as' },
          { hours: 70, name: 'IpASsum' },
          { hours: 1, name: 'asdASDASDfg' },
          { hours: 13, name: 'Sit' },
        ],
      ],
      chart_dataLine: [
        [
          { hours: 238, production: 134, date: 2000 },
          { hours: 938, production: 478, date: 2001 },
          { hours: 1832, production: 1392, date: 2002 },
          { hours: 2092, production: 2343, date: 2003 },
          { hours: 2847, production: 2346, date: 2004 },
          { hours: 2576, production: 2233, date: 2005 },
          { hours: 2524, production: 2325, date: 2006 },
          { hours: 1648, production: 2456, date: 2007 },
          { hours: 2479, production: 2329, date: 2008 },
          { hours: 3200, production: 2438, date: 2009 },
        ],
        [
          { hours: 138, production: 134, date: 1000 },
          { hours: 338, production: 478, date: 1001 },
          { hours: 1831, production: 1331, date: 1001 },
          { hours: 1031, production: 1343, date: 1003 },
          { hours: 847, production: 346, date: 1004 },
          { hours: 1576, production: 1133, date: 1005 },
          { hours: 1514, production: 1315, date: 1006 },
          { hours: 1648, production: 1456, date: 1007 },
          { hours: 1473, production: 1313, date: 1008 },
          { hours: 3100, production: 1438, date: 1009 },
        ],
      ],
      chart_configLine: {
        values: ['hours', 'production'],
        date: {
          key: 'date',
          inputFormat: '%Y',
          outputFormat: '%Y',
        },
        points: false,
        axis: {
          yTicks: 3,
        },
        curve: "curveBasis",
        transition: {
          duration: 350,
          ease: 'easeLinear',
        },
      },
      chart_dataBar: [[
        { hours: 1648, production: 9613, year: '2007' },
        { hours: 2479, production: 6315, year: '2008' },
        { hours: 3200, production: 2541, year: '2009' },
        { hours: 3200, production: 2541, year: '2010' },
        { hours: 900, production: 251, year: '2011' },
        { hours: 2220, production: 241, year: '2012' },
        { hours: 1200, production: 25415, year: '2013' },
      ],[
        { hours: 948, production: 9613, year: '1907' },
        { hours: 2479, production: 6315, year: '1908' },
        { hours: 190, production: 2541, year: '1909' },
        { hours: 1190, production: 2541, year: '1910' },
        { hours: 900, production: 251, year: '1911' },
        { hours: 2219, production: 241, year: '1912' },
        { hours: 1190, production: 25415, year: '1913' },
      ],[
        { hours: 648, production: 9613, year: '2007' },
        { hours: 2479, production: 6315, year: '2008' },
        { hours: 4400, production: 4541, year: '2009' },
        { hours: 200, production: 2541, year: '2010' },
        { hours: 900, production: 251, year: '2011' },
        { hours: 2420, production: 241, year: '2012' },
        { hours: 1200, production: 25415, year: '2013' },
      ]],
      chart_configBar: {
        key: 'year',
        currentKey: '2004',
        values: ['hours'],
        axis: {
          yTicks: 7,
        },
        color: {
          default: '#222f3e',
          current: '#41B882',
        },
      },
    }
  },
  methods: {
    returnYear(years, year) {
      return years[year]
    },
  },
  computed: {},
}
</script>

<style>
</style>