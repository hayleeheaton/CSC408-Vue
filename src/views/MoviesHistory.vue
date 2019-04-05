<template>
    <div class="about pt-4 pb-3">
        <h1>Movie Rentals History</h1>

        <table class="table table-striped">
            <thead>
            <tr>
                <th>Name</th>
                <th>Disc Type</th>
                <th>Rented</th>
                <th>Returned</th>
            </tr>
            </thead>
            <tbody>
            <movie-history-component
                    v-for="(rental, index) in rentals"
                    v-bind="rental"
                    :index="index"
                    :key="rental.id"
            ></movie-history-component>

            </tbody>
        </table>
    </div>
</template>
<script>

    function Rental({id, name, pivot}) {
        this.id = parseInt(pivot.id)
        this.name = name
        this.transaction = pivot
    }

    import MovieHistoryComponent from '@/components/MovieHistoryComponent.vue'

    export default {
        data() {
            return {
                id: null,
                title: '',
                rentals: []
            }
        },
        methods: {
            read() {
                let url = 'https://codeflare.tech/api/movies/' + this.id + '/rentals'
                window.axios.get(url).then(({data}) => {
                    this.title= data[0].title;

                    console.log(this.title);
                    console.log(data[0]);

                    data[0].rentals.forEach(rental => {
                        console.log(rental.pivot)
                        this.rentals.push(new Rental(rental))
                    })
                })
            }
        },
        components: {
            MovieHistoryComponent
        },
        created() {
            this.id = this.$route.params.userId
            this.read()
        }
    }
</script>

<style scoped lang="scss">

    th {
        text-align: left;
    }
</style>
