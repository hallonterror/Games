<!-- src/components/Game.vue -->

<template>
<div class="game-block">
<span>{{title}}</span>
<span>{{price}}</span>
<span>{{currency}}</span>
<span>{{description}}</span>
<img :src="thumbnail" />
<button class="btn btn-primary" v-on:click="getGame()">Fetch game</button>
</div>
</template>

<script>
export default {
  name: 'Game',
  data () {
    return {
      title: '',
      price: '',
      currency: '',
      description: '',
      thumbnail: ''
    }
  },
  methods: {
    getGame () {
      console.log('getGame')

      var invocation = new XMLHttpRequest()
      var url = 'https://store.steampowered.com/api/appdetails?appids=57690&l=sv'

      function handler (response) {
        console.log(response)
      }

      function callOtherDomain () {
        if (invocation) {
          invocation.open('GET', url, true)
          invocation.onreadystatechange = handler
          invocation.send()
        }
      }
      callOtherDomain()

      // this.$http
      //   .get('https://store.steampowered.com/api/appdetails?appids=57690&l=sv', (data) => {
      //     console.log(data)
      //     // this.title = data;
      //   })
      //   .error((err) => console.log(err))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.game-block {
  background: #ccc;
  display: inline-block;
  min-width: 100px;
  min-height: 100px;
}
</style>
