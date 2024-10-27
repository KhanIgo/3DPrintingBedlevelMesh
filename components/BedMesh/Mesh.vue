<script>
import Plotly from "plotly.js";

export default {
  name: "Mesh",
  data() {
    return {
      data: [
        {
          x: [1, 2, 3, 4],
          y: [10, 15, 13, 17],
          type: "scatter",
        },
      ],
      layout: {
        title: "My graph",
      },
    };
  },
  methods: {
    initPlotly() {
      const data = [{
        type: "mesh3d",
        x: [0, 1, 2],
        y: [0, 0, 1],
        z: [0, 2, 0],
        // i: [0, 0, 0],
        // j: [1, 2, 3],
        // k: [2, 3, 1],
        intensity: [0, 0.33, 0.66, 1],
        colorscale: [
          [0, 'rgb(255, 0, 0)'],
          [0.5, 'rgb(0, 255, 0)'],
          [1, 'rgb(0, 0, 255)']
        ]
      }
      ];
      Plotly.newPlot("gd", data);
    }
  },
  mounted() {
    setTimeout(this.initPlotly, 500);
  },
};
</script>

<template>
  <div>
    <h3>Mesh</h3>
      <!--        <Plotly :data="data" :layout="layout" :display-mode-bar="false"></Plotly>-->
        <div id="gd"></div>
  </div>
</template>

<style scoped></style>
