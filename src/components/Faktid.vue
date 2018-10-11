<template>
  <div>
    <h1>Numbrite faktid</h1>
    <p>Huvitavad faktid iga numbri kohta</p>
    <input type="number" min="0" v-model="number">
    <p>{{ data }}</p>
  </div>
</template>

<script>
  const axios = require('axios') //kui tood mujalt andmed sisse
export default {
  name: 'Faktid',
  data () {
    return {
      data: '',
      number: 0
  
    }
  },
  watch: {
    number() {
      if(this.number !== '') {
      
      var url = `http://numbersapi.com/${this.number}`

      axios.get(url)
        .then(response => {
          this.data = response.data
        })
        .catch(error => {
          console.log(error)
        })
       } 
    }
  }
}
</script>
<!--this.users... kasutab siis seda kasutajat, defineerib-->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
