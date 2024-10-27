<template>
  <div droppable class="dropzone" ondrop="onInputDrop">
    <!--    <input class="file-input" type="file" onchange="(e)=>{console.log(e)}" ondrop="(e)=>{console.log(e)}"  />-->
    <span class="label">Перетащите сюда printer.cfg</span>
  </div>
</template>


<script>
export default {
  name: 'DropZone',
  methods: {
    onInputDrop(event) {
      console.log('onDropFile', event);
      return true;
    },
  },
}
</script>


<style scoped>
.dropzone {
  border: dotted 1px grey;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px 10px;
}
.file-input {
  opacity: 0;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
}
.label {
  width: 100%;
  text-align: center;
  position: relative;
  z-index: 1;
}
</style>
