<script>
import Plotly from "plotly.js";

export default {
  name: "Mesh",
  props: {
    meshData: {
      type: Object,
      default: ()=>{},
    },
  },
  watch: {
    mesh(){
      this.initPlotly();
    },
  },
  computed: {
    mesh() {
      console.log('Object.keys(this.meshData)', Object.keys(this.meshData));
      if(Object.keys(this.meshData).length==3) return this.meshData;
      else return this.defaultMeshData;
      // return this.defaultMeshData;
    }
  },
  data() {
    return {
      defaultMeshData: {
        x: [5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5],
        y: [5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5,5.5,11,16.5,22,27.5],
        z: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      },
      layout: {
        title: 'Mt Bruno Elevation',
        autosize: false,
        width: 600,
        height: 800,
        margin: {
          l: 65,
          r: 50,
          b: 65,
          t: 90
        }
      },
    };
  },
  methods: {
    initPlotly() {
      const data = [{
          type: "mesh3d",
          ...this.mesh,
        // intensity: [0, 0.33, 0.66, 1],
        // colorscale: [
        //   [0, 'rgb(255, 0, 0)'],
        //   [0.5, 'rgb(0, 255, 0)'],
        //   [1, 'rgb(0, 0, 255)']
        // ]
      }
      ];
      Plotly.newPlot("gd", data, this.layout);
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
