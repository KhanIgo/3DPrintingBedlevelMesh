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
      if(Object.keys(this.meshData).length) return this.meshData;
      else return this.defaultMeshData;
      // return this.defaultMeshData;
    }
  },
  data() {
    return {
      defaultMeshData: {
        z: [
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
          [0,0,0,0,0],
        ],
      },
      layout: {
        title: 'График неровности стола',
        autosize: false,
        width: 1000,
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
        customdata: ['sdfsdfs', 'dfgdg'],
        ...this.mesh,
        // type: 'surface'
        type: 'heatmap'
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
  <div class="cnt">
    <div id="gd"></div>
  </div>
</template>

<style>
.modebar-btn.plotlyjsicon.modebar-btn--logo {
  display: none !important;
}
.cnt {
  margin-top: 35px;
}
</style>
