<template>

    <div>

        <v-toolbar
        dark
        color="teal darken-4"
        height="63" fixed  
        class="px-5"
        >
            <v-btn icon class="ml-10">
                <v-icon>mdi-basket</v-icon>
            
            <v-toolbar-title class="ml-1">ShopIt</v-toolbar-title>
            </v-btn>

            <v-spacer></v-spacer>

            <v-btn icon class="icon-spacing" href="/login">
                <v-icon >mdi-account-circle</v-icon>
            </v-btn>

            <v-btn icon class="icon-spacing">
                <v-icon>mdi-cart</v-icon>
                <v-badge
                color="green"
                content="6"
                class="mr-2"
                >
                </v-badge>
            </v-btn>

            <v-btn icon class="icon-spacing">
                <v-icon @click="logout">mdi-export</v-icon>
            </v-btn>

            <template v-slot:extension>
                <v-tabs      
                centered
                >
                    <v-tab
                        v-for="tab in tabData"
                        :key="tab.text"  :to="tab.route" class="px-14"
                    >
                        {{ tab.text }}
                    </v-tab>
                </v-tabs>
            </template>
            

        
        </v-toolbar> 
  
   </div>
</template>

<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';
    import Home from "../views/Home.vue";
  
    @Component({
        components: {
            Home
        }
    })
    export default class Header extends Vue {

        private tabData: any = [ 
          { text: "Home", link: "#home", route: "/",  },
          { text: "Products", link: "#proucts", route: "/products" },
          { text: "Blog", link: "#blog", route: "/blog" },
        ];

        logout(){
           this.$store.dispatch('logout');
        }
    }

  
</script>
<style scoped>
    .icon-spacing{
        margin-left: 5px;
    }
</style>