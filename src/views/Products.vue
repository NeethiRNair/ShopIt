<template>
    <v-container fluid class="my-5">
        <v-row>
            <v-col 
            cols="3" 
            class="pl-10">
                <v-card
                height="100%"
                min-height="75vh" 
                outlined>

                    <v-card-title>Filters</v-card-title>
                    <v-divider></v-divider>
                    <v-treeview 
                    class="px-5" 
                    :open="initiallyOpen"
                    :items="categories"
                    hoverable
                    open-on-click
                    activatable>
                    </v-treeview>
                    <v-divider></v-divider>

                    <v-card-title class="mb-n4">Price</v-card-title>
                    <v-slider
                        v-model="maxPriceSelected"
                        class="align-center mx-1"
                        :max="maxPrice"
                        :min="minPrice"
                        dense
                    >
                    </v-slider>
                    <v-row class="mx-1">
                        <v-col>
                            <v-text-field 
                                v-model="minPrice" 
                                outlined 
                                label="Min" 
                                dense ></v-text-field>
                        </v-col>
                        <v-spacer></v-spacer>
                        <v-col>
                            <v-text-field 
                            v-model="maxPriceSelected" 
                            outlined 
                            label="Max"
                            dense></v-text-field>
                        </v-col>
                    </v-row>
                    <v-divider></v-divider>

                    <v-card-title class="mb-n4">Customer Rating</v-card-title>
                    <v-list class="ml">
                        <v-list-item-group
                            v-model="selected"
                            active-class="teal--text text--darken-3"
                            multiple
                        >
                            <template v-for="(item) in [4,3,2,1]">
                            <v-list-item :key="item.title">
                                <template v-slot:default="{ active }">
                                    <v-list-item-action>
                                        <v-checkbox ></v-checkbox>
                                    </v-list-item-action>

                                <v-list-item-content class="ml-n4">
                                    <v-list-item-title>{{item}} & above</v-list-item-title>
                                </v-list-item-content>

                                <v-list-item-action>
                                    <v-list-item-action-text v-text="item.action"></v-list-item-action-text>

                                    <v-icon
                                    v-if="!active"
                                    color="grey lighten-1"
                                    >
                                    mdi-star-outline
                                    </v-icon>

                                    <v-icon
                                    v-else
                                    color="teal darken-3"
                                    >
                                    mdi-star
                                    </v-icon>
                                </v-list-item-action>
                                </template>
                            </v-list-item>

                            </template>
                        </v-list-item-group>
                    </v-list>
                    <v-divider></v-divider>

                    <v-card-title class="mb-n4">Size</v-card-title>
                    <v-list class="ml">
                        <v-list-item-group
                            v-model="selected"
                            active-class="teal--text text--darken-3"
                            multiple
                        >
                            <template v-for="(item) in sizes">
                                <v-list-item :key="item.title">
                                    <template v-slot:default="{ active }">
                                        <v-list-item-action>
                                            <v-checkbox ></v-checkbox>
                                        </v-list-item-action>

                                    <v-list-item-content class="ml-n4">
                                        <v-list-item-title>{{item}}</v-list-item-title>
                                    </v-list-item-content>

                                    <v-list-item-action>
                                        
                                        <v-icon
                                        v-if="!active"
                                        color="grey lighten-1"
                                        >
                                        mdi-star-outline
                                        </v-icon>

                                        <v-icon
                                        v-else
                                        color="teal darken-3"
                                        >
                                        mdi-star
                                        </v-icon>
                                    </v-list-item-action>
                                    </template>
                                </v-list-item>
                            </template>
                        </v-list-item-group>
                    </v-list>
                </v-card>
            </v-col>
                
            <v-col>
                <v-row>
                    <v-col 
                    v-for="card in products"
                    :key="card.name"
                    :cols="3">
                        <v-card>
                            <v-img
                            :src="card.imgUrl"
                            class="white--text align-end"
                            gradient="to bottom, rgba(0,0,0,.01), rgba(0,0,0,.01)"
                            height="250px"
                            >
                                <v-card-title v-text="card.title"></v-card-title>
                            </v-img>
                            <v-card-text class="mb-n8 mx-13 teal--text text--darken-4">{{card.name}}</v-card-text>

                            <v-card-text class="mx-15 teal--text text--darken-4">${{card.price}}</v-card-text>

                        </v-card>
                    </v-col>
                </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>


<script lang="ts">
    import { Component, Vue } from 'vue-property-decorator';
    
    @Component({
        components: {
            
        }
    })
    export default class Products extends Vue {

        private products: any = [];
        private categories: any = [];
        private initiallyOpen: any;
        private maxPrice: any = 1000;
        private minPrice: any = 0;
        private maxPriceSelected: any = 500;
        private settings: any = [];
        private sizes: any = [ "XS", "S", "M", "L", "XL", "XXL", "3XL"]

        mounted(){
           this.products = this.$store.getters.getProducts;
           this.initiallyOpen = ["1"];
           this.categories = this.$store.getters.getCategories;
           console.log(this.products, this.categories);
        }
    }

  
</script>
<style scoped>
    .icon-spacing{
        margin-left: 5px;
    }
</style>