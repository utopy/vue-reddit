<template>
  <div>
      <div class="search-container">

      </div>
    <div class="cards-container">
      <card v-for="post in posts" :post="post"></card>
    </div>
  </div>
</template>
<script>
  import Card from "./card"
  export default {
    data() {
      return {
        posts: []
      }
    },
    components: {
      Card
    },
    mounted() {
      console.log("ciao")
      let request = new XMLHttpRequest;
      request.open("GET", "https://www.reddit.com/r/science/new.json", true);
      request.onload = () => {
        if (request.status >= 200 && request.status < 400) {
          let data = JSON.parse(request.responseText);
          data = data.data.children
          console.log(data.length)
          for (let i = 0; i < data.length; i++) {
            this.posts.push(data[i])
          }
          console.log("---")
          console.log(this.posts)
        } else {
          console.log("error")
        }
      }
      request.onerror = () => {
        console.log("err")
      }

      request.send()
    }
  }

</script>
<style>
  .cards-container {
    width: 400px;
    margin: auto;
  }
  
</style>
