<script>
import Plotly from "plotly.js";

export default {
  name: "Plotly",
  props: {
    type: {
      type: String,
      default: '',
    },
    layout: {
      type: Object,
      default: ()=>{},
    },
    meshData: {
      type: Array,
      default: ()=>[],
    },
  },
  watch: {
    meshData() {
      this.initPlotly();
    },
    type() {
      this.initPlotly();
    },
  },
  methods: {
    initPlotly() {
      const data = [{
        // customdata: ['sdfsdfs', 'dfgdg'],
        // mode: 'lines+markers+text',
        mode: 'lines+markers+text',
        marker: {
          size: [20, 40, 25, 10, 60, 90, 30],
        },
        customdata: [['gngh', "gngh", 'wqxzcb']],
        name: 'group',
        nameposition: 'bottom',
        text: 'group',
        textposition: 'bottom',
        showscale: true,
        showticklabels: true,
        showlegend: true,
        legend: 'ghb;clk;lc',

        ...this.meshData,
        // text: [
        //   ['scscs', 'ssfs', 'sfsfs',0,0],
        //   // [0,0,0,0,0],
        //   // [0,0,0,0,0],
        //   // [0,0,0,0,0],
        //   // [0,0,0,0,0],
        // ],
        type: this.type,
        // type: 'heatmap'
      }
      ];
      Plotly.newPlot("gd", data, this.layout);
    },
  },
  mounted() {
    setTimeout(this.initPlotly, 500);
  },
}
</script>

<template>
  <div id="gd"></div>
</template>

<style scoped>

</style>
