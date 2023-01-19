<script>
import axios from 'axios';
export default {
  name: 'App',
  data() {
    return {

    }
  },
  components: {

  },
  created() {

  },

  methods: {
    getPosts() {
      axios.get('http://localhost:8000/api/posts').then(resp => {
        console.log(resp);
      })
    }
  }
}

</script>

<template>
  <h1>Pagina di Front Office</h1>
</template>

<style lang="scss">
@use './styles/general.scss' as *;
</style>