<template>
      <v-carousel
    cycle
    height="400"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item
      v-for="(item,i) in images"
      :key="i"
      :src="item.src"
    >
      
    </v-carousel-item>
  </v-carousel>
</template>

<script lang="ts">
  import { Component, Vue, Watch } from 'vue-property-decorator';

  
  @Component({
     components: {
        
      }
  })
  export default class Carousel extends Vue {
      private images: any = [{
          src: "https://loving-leavitt-9cb65b.netlify.app/static/img/slider4.0e80ba7.jpg"
      },
      {
          src: "https://loving-leavitt-9cb65b.netlify.app/static/img/slider1.8a3a968.jpg"
      },
      {
          src: "https://loving-leavitt-9cb65b.netlify.app/static/img/slider2.b3a6509.jpg"
      },
      {
          src: "https://loving-leavitt-9cb65b.netlify.app/static/img/slider3.6f27a30.jpg"
      }]
  }

</script>