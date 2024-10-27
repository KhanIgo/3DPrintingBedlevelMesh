<script>
import InputContainer from '~/components/BedMesh/InputContainer.vue'
import Mesh from '~/components/BedMesh/Mesh.vue'
export default {
  name: 'Container',
  components: {InputContainer, Mesh},
  data() {
    return {
      inputData: [],
      meshData: [],
      meshOffset: 5.5,
    };
  },
  computed: {
    preparedMeshData() {
      const X = [];
      const Y = [];
      const Z = [];
      this.meshData.map(row=>{
        row.map(item=>{
          X.push(item.X);
          Y.push(item.Y);
          Z.push(item.Z);
        });
      });
      if(X.length && Y.length && Z.length ) return {x:X.reverse(), y:Y.reverse(), z:Z.reverse()};
      return {};
    },
  },
  watch: {
    inputData (){
      this.inputDataToMeshData();
    },
  },
  methods: {
    onDataInput(data){
      console.log( 'onDataInput', data);
      this.inputData = data;
    },
    inputDataToMeshData() {
      const res =  this.inputData.map( (item, index) => {
        return this.inputRowToMeshRow(item, index);
      });
      console.log('inputDataToMeshData', res);
      this.meshData = res;
    },
    inputRowToMeshRow(row, rowIndex) {
      return row.map((item, index)=>{
        return this.inputItemToMeshItem(item, index, rowIndex);
      })
    },
    inputItemToMeshItem(item, itemIndex, rowIndex) {
      console.log('item, itemIndex, rowIndex', {item, itemIndex, rowIndex});
      const res = {
        Y: (rowIndex+1)*this.meshOffset,
        X: (itemIndex+1)*this.meshOffset,
        Z: item,
      }
      return res;
    },
  },
}
</script>

<template>
  <div>
    <h1>Container</h1>
    <Mesh :mesh-data="preparedMeshData" />
    <input-container @onMeshDatainput="onDataInput" />
  </div>
</template>

<style scoped>

</style>
