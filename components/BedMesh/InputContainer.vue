<script>
// import DropZone from '~/components/BedMesh/DropZone.vue'
export default {
  name: 'InputContainer',
  // components: { DropZone },
  data() {
    return {
      meshString: '',
      meshData: {}
    }
  },
  methods: {
    onChange(event) {
      console.log('onChange', event.currentTarget.value);
      let data = event.currentTarget.value.split("#*#");
      data = data.map(item=>{
        return item.trim().replaceAll(' ', '').split(',').map(i=>{ return parseFloat(i)} );
      }).filter(item=>{
        return !!item && item.length==5;
      });
      console.log('data', data);
      const isValidData = this.isDataValid(data);
      if(isValidData) this.$emit('onMeshDatainput', data);
    },
    isDataValid(data) {
      const isDataIsArray = data.length == 5;
      let isEachIsArray = true;
      data.forEach(item=>{
        if(!item || item.length!=5) isEachIsArray = false;
      });
      return isDataIsArray && isEachIsArray;
    }
  },
}
</script>

<template>
  <div class="cnt">
    <p class="title">Данные Mesh</p>
    <textarea class="textarea" @change="onChange" placeholder="Вставьте mesh данные из printer.cfg"></textarea>
<!--    <div class="cnt">-->
<!--      <DropZone />-->
<!--    </div>-->
  </div>
</template>

<style scoped>
  .textarea {
    font-size: 12px;
    height: 7em;
    width: 100%;
    max-width: 550px;
    resize: none;
    border: solid 1px grey;
    border-radius: 5px;
    padding: 10px;
  }
  .title {
    margin-bottom: 15px;
  }
  .cnt {
    border-bottom: solid 1px grey;
    padding-bottom: 25px;
  }
</style>
