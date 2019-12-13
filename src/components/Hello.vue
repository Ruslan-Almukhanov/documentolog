<template>
     <div class="article">
          <h1>
               Latest films
          </h1>
          <ul class="lists">
               <li v-for="post in posts">
                    <img :src="post.Poster" alt="poster">
                    <h2>
                         {{post.Title}} 
                    </h2>
                    <router-link
                         active-class="is-active"
                         class="link"
                         :to="{ name: 'post', params: { imdbID: post.imdbID } }">
                         Learn more<span><i class="fas fa-arrow-circle-right"></i></span>
                    </router-link>
               </li>
             
          </ul>
          
     </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      posts: null,
      endpoint: 'http://www.omdbapi.com/?i=tt3896198&apikey=99f121da&s=movie',
    }
  },

  created() {
    this.getAllPosts();
  },

  methods: {
    getAllPosts() {
      axios.get(this.endpoint)
        .then(response => {
          this.posts = response.data.Search;
        })
        .catch(error => {
          console.log('-----error-------');
          console.log(error);
        })
    }
  }
}
</script>
<style>
ul, li {
	display: block;
	padding: 0;
	margin: 20px; 
}

li {
     width: 200px;
}

h2 {
     font-size: 20px;
     margin-top: 10px;
}

.lists {
     margin-top: 50px;
     display: flex;
     flex-wrap: wrap;
}

.lists a {
     display: flex;
     color: #13AABF
}

.lists a i {
     transition: all 0.3s ease;
}

.lists a:hover i {
     color: #0a546b;
     transform: translateX(100%);
     transition: all 0.3s ease;
}

.lists img {
     width: 200px;
     height: 250px;
}

.article {
     background-color: #fff;
     padding: 30px;
}
</style>

