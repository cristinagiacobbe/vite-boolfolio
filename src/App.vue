<script>
import axios from 'axios';

export default{
  name: 'App',
  data(){
    return{
      base_api_url: 'http://127.0.0.1:8000',
      projects_endpoint: '/api/projects',
      projects : ''
    }
  },
  mounted(){
    const url = this.base_api_url + this.projects_endpoint
    console.log(url);
    axios
    .get(url)
    .then(resp => {
      console.log(resp);
      this.projects = resp.data.results
    })
    .catch(err => {
      console.error(err)
    })
    },
    
  }

</script>

<template>
  <h1>Projects</h1>
  <div class="container">
    <div class="row">
      <div class="col" v-for="project in projects">
        <div class="card">
        {{ project.title }}
        </div>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>
