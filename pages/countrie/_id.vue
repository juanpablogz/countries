<template>
<div>
    <b-container>
        <b-row class="countrie">
            <!-- {{countrie[0].flag}} -->
            <b-col cols="6">
                <img :src="countrie.flag" alt="portada" class="flag">
            </b-col>
            <b-col cols="9">
                <b-card>
                    <p>capital: {{countrie.capital}} </p>
                    <p>Region: {{countrie.region}}</p>
                    <p>Poblacion: {{countrie.population}}</p>
                    <p>Area: {{countrie.area}} </p>
                </b-card>
            </b-col>
        </b-row>
    </b-container>
</div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
    countrie: [],
    img: '',
    currencies: []
    }
  },
  mounted () {
    this.asyncData()
  },
  methods: {
      asyncData () {
        const cors = "https://cors-anywhere.herokuapp.com/"
        return axios.get(`${cors}https://restcountries.eu/rest/v2/name/${this.$route.params.id}?fullText=true`)
        .then(res => {
          console.log(res)
          this.countrie = res.data[0];
          this.img = res.data[0].flag;
          this.currencies = countrie.currencies
        })
      }
  }
}
</script>

<style scoped>
.flag {
    width: 500px;
}
@media (max-width: 600px) {
.flag {
    width: 280px;
}
}
</style>