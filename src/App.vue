<template>
  <div id="app" class="container-fluid">
    <div class="row m-4">
      <app-search v-on:newsChanged="getNews"/>
    </div>
    <div class="m-2">
      <label for="title">Title </label>
      <input type="radio" id="title" value="title" v-model="sortCriteria">
      <label for="author">Author </label>
      <input type="radio" id="author" value="author" v-model="sortCriteria">
    </div>
    <div class="row">
      <app-article v-for="(article, index) in sortedArticles" :key="index" :data="article" />
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Article from './components/Article.vue';
import Search from './components/Search.vue';

export default {
  name: 'App',
  components: {
    'app-article': Article,
    'app-search': Search,
  },
  data(){
    return {
      articles: [
        
      ],
      searchQ: 'science',
      sortCriteria: '',
    }
  },
  methods: {
    getNews(query) {
      var url = 'https://newsapi.org/v2/everything?' + 'q=' + query + '&' + 'apiKey=e04c8f085de04a4f8ec929ef1499d6dc';
      var req = new Request(url);
      fetch(req)
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          console.log(data);
          this.articles = data.articles;
        }).catch((err) => {
          console.log(err);
        })

      this.searchQ = '';
      this.sortCriteria = '';
    },

    sortBy(arr, sortCrit){
      return arr.sort((a, b) => {
        if (a[sortCrit] > b[sortCrit]) return 1;
        if (a[sortCrit] < b[sortCrit]) return -1;
        return 0;
      })
    }
  },
  computed: {
    sortedArticles() {
      if(this.sortCriteria){
        return this.sortBy(this.articles, this.sortCriteria);
      } else {
        return this.articles;
      }
      
    }
  },
  mounted() {
    this.getNews(this.searchQ);
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
