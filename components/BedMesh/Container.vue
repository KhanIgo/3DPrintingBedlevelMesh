<script>
import InputContainer from '~/components/BedMesh/InputContainer.vue'
import Mesh from '~/components/BedMesh/Mesh.vue'
export default {
  name: 'Container',
  components: {InputContainer, Mesh}
}
</script>

<template>
  <div>
    <h1>Container</h1>
    <Mesh />
    <input-container />
  </div>
</template>

<style scoped>

</style>
