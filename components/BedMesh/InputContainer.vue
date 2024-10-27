<script>
export default {
  name: 'InputContainer',
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
  <div>
    <h2>InputContainer</h2>
    <textarea @change="onChange"></textarea>
  </div>
</template>

<style scoped>

</style>
