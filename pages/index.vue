<template>
  <div class="container">
    <div>
      <b-container>
        <b-row>
          <b-col md="4" sm="12" v-for="countrie in countries" :key="countrie.id">
            <b-card :title="countrie.name" :img-src="countrie.flag" img-alt="img" img-top style="max-width:20rem">
              <p class="card-text">
              </p>
              <nuxt-link :to="`countrie/${countrie.name}`" class="btn btn-primary">Ver más</nuxt-link>
            </b-card>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
    countries: []
    }
  },
  mounted () {
    this.asyncData()
  },
  methods: {
      asyncData () {
        const cors = "https://cors-anywhere.herokuapp.com/"
        return axios.get(`${cors}https://restcountries.eu/rest/v2/all`)
        .then(res => {
          console.log(res)
          this.countries = res.data;
        })
      }
  }
}
</script>

<style>

</style>
