<script>
import InputContainer from '~/components/BedMesh/InputContainer.vue'
import Mesh from '~/components/BedMesh/Mesh.vue'
import TableDescription from '~/components/BedMesh/TableDescription.vue'
export default {
  name: 'Container',
  components: {InputContainer, Mesh, TableDescription},
  data() {
    return {
      inputData: [],
      meshData: [],
      meshOffset: 5.5,
      min: 0,
      max: 0,
    };
  },
  computed: {
    preparedMeshData() {
      if(this.inputData.length) {
        let z = [...this.inputData];
        z.reverse();
        z = z.map(row=>{
          return row.reverse();
        });
        return {z};
      }
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
      let tempData = [];
      const sortByMin = (a,b)=>{
        return a-b;
      }
      const sortByMax = (a,b)=>{
        return b-a;
      }

      data.map(item=>{
        tempData = tempData.concat(item);
      });
      tempData.sort(sortByMin);
      this.min = tempData[0];
      tempData.sort(sortByMax);
      this.max = tempData[0];
    },
    inputDataToMeshData() {
      const data = [...this.inputData].reverse();
      const res =  data.map( (item, index) => {
        return this.inputRowToMeshRow(item, index);
      });
      this.meshData = res;
    },
    inputRowToMeshRow(row, rowIndex) {
      return row.map((item, index)=>{
        return this.inputItemToMeshItem(item, index, rowIndex);
      })
    },
    inputItemToMeshItem(item, itemIndex, rowIndex) {
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
  <div class="row container">
    <h1>График карты стола для Adventurer 5M / 5M Pro</h1>
    <input-container @onMeshDatainput="onDataInput" />
    <Mesh :mesh-data="preparedMeshData" />
    <table-description :min="min" :max="max" />
  </div>
</template>

<style scoped>
  .container {
    padding: 35px 0 35px;
  }
  h1 {
    width: 100%;
    text-align: center;
    margin-bottom: 65px;
  }
</style>
