<template>
  <Carousel />
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import Carousel from "../components/Carousel.vue";
  
  @Component({
     components: {
        Carousel
      }
  })
  export default class Home extends Vue {
  }

</script>
