<template>
    <div class="card" style = "width: 20rem">
        <img :src="this.imageUrl" class="card-img-top">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <h6 class="card-text">{{ rating }}</h6>
        </div>
        <div id = "card-links">
            <button class ="btn-view"><router-link :to="'/movies-details/' + this.id">View</router-link></button>
            <button class="btn-rental"><router-link :to="'/movies-details/' + this.id + '/rented'">Rentals</router-link></button>
        </div>
    </div>
</template>

<script>
export default {
    data () {
      return {}
    },
    computed: {
        /* Build URL for image */
        imageUrl: function () {
            return "http://codeflare.tech/images/movie_" + this.id + ".jpg";
        }
    },
    methods: {
      view () {
        // this.$emit('view', this.id);
        console.log('Component Viewing id:' + this.id)

        // this.$router.push({ name: 'customer-details', params: { id: 3 } })
        let myRoute = '/movie-details/3';
        this.$router.push(myRoute);
      },
      rentals () {
        this.$emit('rentals', this.id);
      }
    },
    props: ['id', 'title', 'rating', 'length', 'onBluRay', 'onDVD']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.card{
    margin-top: 5px;
    margin-bottom: 5px;
}

.card-title{
    text-align: center;
}

.card-text{
    text-align: center;
}

#card-links {
    padding: 1rem;
}

.btn-view {
    margin-right: 5px;
    border-radius: 5px;
    border-color: #ffd521;
    background-color: #ffd521;

a {
    color: #67917b;
    }
}

.btn-rental {
    margin-left: 5px;
    border-radius: 5px;
    border-color:#67917b;
    background-color: #67917b;
a {
    color: #ffd521;
    }
}

</style>
