<template lang="html">
  <div class="post d-flex" v-if="post">
    <div class="breadcrumbs">
    <router-link
          :to="{ name: 'home'}">
          <span><i class="fas fa-arrow-circle-left"></i></span>
          Back
    </router-link>
  </div>
    <div class="post__img">
      <img :src="post.Poster" alt="poster">
    </div>
    <div class="post__desc">
      <h1 class="post__title">{{ post.Title }}</h1>
      <div class="d-flex">
        <p>Genre: </p>
         <p class="post__genre">{{ post.Genre }}</p>
      </div>
      <div class="d-flex">
        <p>Public date: </p>
        <p class="post__id">{{ post.Year }}</p>
      </div>
      <div class="d-flex">
        <p>Director: </p>
        <p class="post__id">{{ post.Director }}</p>
      </div>
      <div class="d-flex">
        <p>Actors: </p>
        <p class="post__id">{{ post.Actors }}</p>
      </div>
      <div class="d-flex">
        <p>Runtime: </p>
        <p class="post__id">{{ post.Runtime }}</p>
      </div>
      <div class="d-flex">
        <p>Country: </p>
        <p class="post__id">{{ post.Country }}</p>
      </div>
      <div class="d-flex">
        <p>Language: </p>
        <p class="post__id">{{ post.Language }}</p>
      </div>
      <div class="d-flex">
        <p>Production: </p>
        <p class="post__id">{{ post.Production }}</p>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  props: ['imdbID'],
  data() {
    return {
      post: null,
      endpoint: 'http://www.omdbapi.com/?apikey=99f121da&i=',
    }
  },
  methods: {
  getPost(imdbID) {
    axios(this.endpoint + imdbID)
      .then(response => {
        this.post = response.data
      })
      .catch( error => {
        console.log(error)
      })
  }
},
  
created() {
  this.getPost(this.imdbID);
},
watch: {
  '$route'() {
    this.getPost(this.imdbID);
  }
}
}
</script>
<style>
.post {
  background-color: #fff;
  padding: 30px;
}

.breadcrumbs a {
  display: flex;
    color: #13AABF;
    margin-right: 15px;
}

.d-flex {
  display: flex;
  align-items: center;
}

.post__desc .d-flex p:first-child {
  margin-right: 10px;
  font-size: 18px;
  font-weight: bold;
}

.post__desc .d-flex p:last-child {
  font-size: 17px;
  color: #807b7b;
}

.post__img {
  margin-right: 20px;
}
</style>

