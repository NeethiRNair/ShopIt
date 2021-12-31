<template>
  <v-app>
    <v-main>
      <Header/>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
  import { Component, Vue, Watch } from 'vue-property-decorator';
  import Header from './components/Header.vue';

  @Component({
     components: {
        Header
      }
  })
  export default class App extends Vue {
  }

</script>
