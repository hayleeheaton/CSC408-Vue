<template>
    <div class="pt-4 pb-3">
        <h3>Movie Details</h3>
        <div class="card" style="width: 50%;">
            <div class="card-body">
                <img :src="this.imageUrl" class="thumbnail">
                <h5 class="card-title">{{movie.title}} - {{ movie.id }}</h5>
                <h6 class="card-subtitle mb-2 text-muted">{{movie.rating}}</h6>
                <p class="card-text">Length: {{ movie.length }}</p>
                <p class="card-text">Description: {{ movie.description }}</p>
                <p class="card-text">BluRay Inventory {{ movie.onBluRay }}</p>
                <p class="card-text">DVD Inventory {{ movie.onDVD }}</p>
            </div>
        </div>

    </div>
</template>
<script>

  function Movie ({ id, title, rating, length, description, onBluRay, onDVD, updated_at }) {
      this.id = parseInt(id)
      this.title = title
      this.rating = rating
      this.length = length
      this.description = description
      this.onDVD = onDVD
      this.onBluRay = onBluRay
      this.updated_at = updated_at

  }

  export default {
    data () {
      return {
        id: null,
        movie: Object
      }
    },
    methods: {
      read () {
        let url = 'https://codeflare.tech/api/movies/' + this.id
        window.axios.get(url).then(({ data }) => {
          this.movie = data;
        })
      }
    },
    computed: {
        /* Build URL for image */
        imageUrl: function () {
            return "http://codeflare.tech/images/movie_" + this.id + ".jpg";
        },

      /* Make a pretty date for showing last_update */
      updated: function(){
        var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: 'numeric', minute: 'numeric' };
        var today  = new Date(this.customer.updated_at);
        return today.toLocaleString("en-US", options);
      }
    },
    components: {

    },
    created () {
      this.id = this.$route.params.userId
      this.read()
    }
  }
</script>

<style>
    .card {
        margin: auto;
    }
    .card-body {
        text-align: left;
    }
</style>
