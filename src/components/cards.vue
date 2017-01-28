<template>
  <div>
    <div class="search-container">
      <input type="text" placeholder="Search for a subreddit..." v-model="searchInput" v-on:keyup.enter="searchSubreddit" v-on:click="showFilters = true">
    </div>
    <ul class="filters-container" v-if="showFilters">
      <li v-for="(filter, index) in filters"><span v-on:click="changeFilter(filter)">{{filter}}</span></li>
    </ul>
    <div class="cards-container">
      <card v-if="noPosts" v-for="post in posts" :post="post"></card>
    </div>
  </div>
</template>
<script>
  import Card from "./card"
  export default {
    data() {
      return {
        posts: [],
        noPosts: true,
        searchInput: '',
        showFilters: false,
        filters: ['new', 'rising', 'controvertial', 'top', 'gilded', 'wiki', 'ads']
      }
    },
    methods: {
      changeFilter: function(filter){
        console.log("received")
        console.log(this.searchInput)
        let request = new XMLHttpRequest;
        request.open("get", "https://www.reddit.com/r/" + this.searchInput + "/" + filter + "/.json", true)
        request.onload = () => {
          if (request.status >= 200 && request.status < 400) {
            let data = JSON.parse(request.responseText);
            data = data.data.children
            this.posts = [];
            for (let i = 0; i < data.length; i++) {
              this.posts.push(data[i])
            }
          }
        }
				request.send()
      },
      searchSubreddit: function () {
        console.log("received")
        console.log(this.searchInput)
        let request = new XMLHttpRequest;
        request.open("get", "https://www.reddit.com/r/" + this.searchInput + ".json", true)
        request.onload = () => {
          if (request.status >= 200 && request.status < 400) {
            let data = JSON.parse(request.responseText);
            data = data.data.children
            this.posts = [];
            for (let i = 0; i < data.length; i++) {
              this.posts.push(data[i])
            }
          }
        }

        request.send()
      }
    },
    components: {
      Card
    },
    mounted() {
      console.log("ciao")
      let request = new XMLHttpRequest;
      request.open("GET", "https://www.reddit.com/r/science.json", true);
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
  .search-container {
    width: 100%;
    margin: auto;
  }
  
  .search-container input {
    width: 100%;
    padding-top: 10px;
    padding-bottom: 10px;
    border: none;
    background: #ccc;
    margin: 0;
  }
  
  .search-container input:focus {
    outline: none;
  }
  
  .cards-container {
    width: 100%;
  }
  
  .filters-container {}
  
  .filters-container ul {
    list-style: none;
    float: left;
    margin: 20px;
  }
  
  .filters-container li {
    display: inline-block;
    margin-right: 20px;
    padding: 5px 10px;
    font-size: 12px;
    background-color: rgba(33, 33, 33, 0.19);
  }

</style>
