<!-- src/components/Game.vue -->

<template>
<div class="game-block">
<span>{{title}}</span>
<span>{{price}}</span>
<span>{{currency}}</span>
<span>{{description}}</span>
<img src="{{thumbnail}}" />
<button class="btn btn-primary" v-on:click="getGame()">Fetch game</button>
<div>
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
      this.$http
        .get('https://store.steampowered.com/api/appdetails?appids=57690&l=sv', (data) => {
          console.log(data)
          // this.title = data;
        })
        .error((err) => console.log(err))
    }
  }
}
</script>
