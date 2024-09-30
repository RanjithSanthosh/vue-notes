<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{name:'about'}">About</router-link>
    <router-link to="/testRouter">  
      testRouter</router-link>
     
    </nav>
    <div v-for="job in jobs" :key="job.id">
      <h1>{{ job.name }}</h1>
      <h1>{{ job.reg }}</h1>
    </div>
  <router-view/> 
  </template>
<script>
export default{
  data(){
    return{
      jobs:[]
    }
  },
  mounted(){
  fetch('http://localhost:3000/jobs')
  .then(res =>res.json())
  .then(data =>this.jobs = data)
  .catch(err =>console.log(err.message))
}
}

</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
