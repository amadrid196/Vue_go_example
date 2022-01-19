<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h1 v-for ="lg in lenguaje" :key="lg.Name">{{lg.Name}} <h5>{{lg.Lenguaje}}</h5></h1>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      lenguaje: []
    }
  },

  methods: {
    getContries: function () {
      var url = 'http://localhost:8080/contries'
      axios
        .get(url)
        .then((response) => {
          console.log(response)
          this.lenguaje = response.data
        })
        .catch((err) => {
          console.log(err)
        })
    },

    postContries: function () {
      var url = 'http://localhost:8080/contries'
      axios
        .post(url, {
          Name: 'Honduras',
          Lenguaje: 'Español'
        })
        .then((response) => {
          console.log(response)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  created () {
    this.getContries()
    this.postContries()
  },

  mounted () {
    this.getContries()
  }
}
</script>
