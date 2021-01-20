<template>
  <v-bottom-navigation
    v-model="value"
    :background-color="color"
    dark
    shift
  >
    <v-btn>
      <span>Video</span>
      <br>
      <v-icon>mdi-television-play</v-icon>
    </v-btn>

    <v-btn>
      <span>Music</span>

      <v-icon>mdi-music-note</v-icon>
    </v-btn>

    <v-btn>
      <span>Book</span>

      <v-icon>mdi-book</v-icon>
    </v-btn>

    <v-btn>
      <span>Image</span>

      <v-icon>mdi-image</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
// import NavBar from './components/NavBar'

export default {
  name: 'App',

  components: {
    // NavBar
  },

  data: () => ({ value: 0 }),

  computed: {
    color () {
      switch (this.value) {
        case 0: return 'blue-grey'
        case 1: return 'teal'
        case 2: return 'brown'
        case 3: return 'indigo'
        default: return 'blue-grey'
      }
    },
  },
};
</script>

<style >
  .hhh{
    display: block;
  }
</style>
