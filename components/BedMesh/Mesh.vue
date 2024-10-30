<script>
import Plotly  from '~/components/BedMesh/Plotly.vue'
export default {
  name: "Mesh",
  components: { Plotly },
  props: {
    meshData: {
      type: Object,
      default: ()=>{},
    },
    type: {
      type: String,
      default: '',
    },
  },
  watch: {
    mesh(){},
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
        },
      },
    };
  },
  methods: {
    onSetView3d() {
      this.$emit('set-type', 'surface')
    },
    onSetViewFlat() {
      this.$emit('set-type', 'heatmap')
    },
  },

};
</script>

<template>
  <div class="cnt">
    <div class="mesh-btns">
      <button class="ui-btn" @click="onSetView3d">3D визуализация</button>
      <button class="ui-btn" @click="onSetViewFlat">Плоский вид</button>
    </div>
    <plotly :type="type" :mesh-data="mesh" :layout="layout" />
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
