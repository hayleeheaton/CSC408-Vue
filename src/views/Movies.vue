<template>
  <div class="container">
    <div class="content">
    <h1>Movies</h1>
    <div class= "row">
      <!-- Listing Database operation -->
      <movie-component
              v-for="(movie, index) in movies"
              v-bind="movie"
              :index="index"
              :key="movie.id"
              @view="view"
              @rentals="rentals">
      </movie-component>
  </div>
  </div>
  </div>
</template>
<script>

    function Movie ({ id, title, rating, length, onDVD, onBluRay, updated_at }) {
        this.id = parseInt(id)
        this.title = title
        this.rating = rating
        this.length = length
        //this.description = description
        this.onDVD = onDVD
        this.onBluRay = onBluRay
        this.updated_at = updated_at
    }

    /* Go get the code for the movie-component tag that is in the template */
    import MovieComponent from '@/components/MovieComponent.vue'

    export default {
        data () {
            return {
                movies: []
            }
        },
        methods: {

            read () {
                this.movies = []
                window.axios.get('https://codeflare.tech/api/movies').then(({ data }) => {
                    data.forEach(movie => {
                    this.movies.push(new Movie(movie))
            })
            })
            },
            view (id) {
            },
            rentals (id) {
            }
    },

        components: {
            MovieComponent
        },
        created () {
            this.read()
        }
    }
</script>

<style>

</style>
