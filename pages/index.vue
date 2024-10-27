<template>
  <container />
</template>

<script>
import Container from '~/components/BedMesh/Container.vue'
export default {
  name: 'IndexPage',
  components: {Container}

}
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&family=Rubik+Doodle+Shadow&display=swap');
  *{
    margin: 0;
    padding: 0;
  }

    .roboto-thin {
      font-family: "Roboto", sans-serif;
      font-weight: 100;
      font-style: normal;
    }

    .roboto-light {
      font-family: "Roboto", sans-serif;
      font-weight: 300;
      font-style: normal;
    }

    .roboto-regular, body {
      font-family: "Roboto", sans-serif;
      font-weight: 400;
      font-style: normal;
    }

    .roboto-medium {
      font-family: "Roboto", sans-serif;
      font-weight: 500;
      font-style: normal;
    }

    .roboto-bold {
      font-family: "Roboto", sans-serif;
      font-weight: 700;
      font-style: normal;
    }

    .roboto-black {
      font-family: "Roboto", sans-serif;
      font-weight: 900;
      font-style: normal;
    }

    .roboto-thin-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 100;
      font-style: italic;
    }

    .roboto-light-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 300;
      font-style: italic;
    }

    .roboto-regular-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 400;
      font-style: italic;
    }

    .roboto-medium-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 500;
      font-style: italic;
    }

    .roboto-bold-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 700;
      font-style: italic;
    }

    .roboto-black-italic {
      font-family: "Roboto", sans-serif;
      font-weight: 900;
      font-style: italic;
    }

    .row{
      width: 100%;
      display: flex;
      flex-wrap: wrap;
    }
    .cnt {
      width: 100%;
      max-width: 1500px;
      padding-left: 15px;
      padding-right: 15px;
    }
</style>
