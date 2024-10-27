<script>
export default {
  name: 'TableDescription',
  props: {
    min: {
      type: Number,
      default: 0,
    },
    max: {
      type: Number,
      default: 0,
    },
  },
}
</script>

<template>
  <div class="cnt">
    <p v-if="min">Минимум: <b>{{min}}</b></p>
    <p v-if="max">Максимум: <b>{{max}}</b></p>
    <p v-if="min && max">Перепад: <b>{{max - min}}</b></p>
  </div>
</template>

<style scoped>

</style>
