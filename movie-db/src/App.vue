<template>
  <div class="container">
    <div class="Search">
      <input v-model="searchTerm" placeholder="Search for a movie">
      <button @click="fetchMovieByTitle(searchTerm)">Search</button>
    </div>
    <div v-if="movie.Title" class="Poster">
      <img :src="movie.Poster" alt="Movie Poster">
    </div>
    <div v-if="movie.Title" class="Actors-Writers">
      <div class="Actors">
        <h3>Actors</h3>
        <p>{{ movie.Actors }}</p>
      </div>
      <div class="Writers">
        <h3>Writers</h3>
        <p>{{ movie.Writer }}</p>
      </div>
    </div>
    <div v-if="movie.Title" class="Plot">
      <h3>Plot</h3>
      <p>{{ movie.Plot }}</p>
    </div>
    <div v-if="movie.Title" class="About">
      <div class="Title">
        <h3>Title</h3>
        <p>{{ movie.Title }}</p>
      </div>
      <div class="Year">
        <h3>Year</h3>
        <p>{{ movie.Year }}</p>
      </div>
      <div class="Genre">
        <h3>Genre</h3>
        <p>{{ movie.Genre }}</p>
      </div>
      <div class="Director">
        <h3>Director</h3>
        <p>{{ movie.Director }}</p>
      </div>
      <div class="Runtime">
        <h3>Runtime</h3>
        <p>{{ movie.Runtime }}</p>
      </div>
      <div class="Language">
        <h3>Language</h3>
        <p>{{ movie.Language }}</p>
      </div>
      <div class="Country">
        <h3>Country</h3>
        <p>{{ movie.Country }}</p>
      </div>
    </div>
    <div v-if="movie.Title" class="BoxOffice">
      <h3>BoxOffice</h3>
      <p>{{ movie.BoxOffice }}</p>
    </div>
    <div v-if="movie.Title" class="Production"></div>
    <div v-if="movie.Title" class="Website">
      <h3>Website</h3>
      <p>{{ movie.Website }}</p>
    </div>
    <div v-if="movie.Title" class="Random">
      <div class="Awards">
        <h3>Awards</h3>
        <p>{{ movie.Awards }}</p>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      movie: {},
      searchTerm: ''
    }
  },
  methods: {
    fetchMovieByTitle(title) {
      fetch(`http://www.omdbapi.com/?apikey=8481f0a&t=${title}`)
        .then(response => response.json())
        .then(data => {
          this.movie = data;
          console.log(this.movie)
        })
        .catch(error => {
          console.log(error);
        });
    }
  }
}
</script>
