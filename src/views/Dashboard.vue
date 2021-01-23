<template >
<div>
    <h1 class="text-center mt-4 font-weight-light">Dashboard</h1>
    <v-card>
        <v-card-title>
        <v-row>
          <v-col
            cols="12"
            sm="3"
            class="center"
          >
        <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search"
        ></v-text-field>
          </v-col>
        </v-row>
        </v-card-title>
        <v-divider class="mt-4"></v-divider>
        <v-data-table
            :search="search"
            :headers="headers"
            :items="desserts"
            :items-per-page="5"
            @click:row="getRowInfo"
            class="elevation-1"
    ></v-data-table>
        <v-snackbar
        v-model="snackbar"
        >
            You Have Selected {{ currentItem }}
        <template v-slot:action="{ attrs }">
            <v-btn
            color="pink"
            text
            v-bind="attrs"
            @click="snackbar = false"
            >
            Close
            </v-btn>
        </template>
        </v-snackbar>
    </v-card>
</div>
</template>
<script>
  export default {
    data () {
      return {
        search:'',
        snackbar :false,
        currentItem:'',
        headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Calories', value: 'calories' },
          { text: 'Fat (g)', value: 'fat' },
          { text: 'Carbs (g)', value: 'carbs' },
          { text: 'Protein (g)', value: 'protein' },
          { text: 'Iron (%)', value: 'iron' },
        ],
        desserts: [
          {
            name: 'Frozen Yogurt',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: '1%',
          },
          {
            name: 'Ice cream sandwich',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: '1%',
          },
          {
            name: 'Eclair',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: '7%',
          },
          {
            name: 'Cupcake',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            iron: '8%',
          },
          {
            name: 'Gingerbread',
            calories: 356,
            fat: 16.0,
            carbs: 49,
            protein: 3.9,
            iron: '16%',
          },
          {
            name: 'Jelly bean',
            calories: 375,
            fat: 0.0,
            carbs: 94,
            protein: 0.0,
            iron: '0%',
          },
          {
            name: 'Lollipop',
            calories: 392,
            fat: 0.2,
            carbs: 98,
            protein: 0,
            iron: '2%',
          },
          {
            name: 'Honeycomb',
            calories: 408,
            fat: 3.2,
            carbs: 87,
            protein: 6.5,
            iron: '45%',
          },
          {
            name: 'Donut',
            calories: 452,
            fat: 25.0,
            carbs: 51,
            protein: 4.9,
            iron: '22%',
          },
          {
            name: 'KitKat',
            calories: 518,
            fat: 26.0,
            carbs: 65,
            protein: 7,
            iron: '6%',
          },
        ],
      }
    },
    methods:{
        getRowInfo(event){
            this.snackbar = true;
            this.currentItem = event.name +" & Iron is  "+event.iron;
        }
    }
  }
</script>
<style >
    
</style>