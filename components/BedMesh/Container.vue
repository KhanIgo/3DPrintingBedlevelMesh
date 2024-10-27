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
      meshOffset: 2,
    };
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
    <Mesh />
    <input-container @onMeshDatainput="onDataInput" />
  </div>
</template>

<style scoped>

</style>
