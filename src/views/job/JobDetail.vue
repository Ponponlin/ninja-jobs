<template>
<div v-if="job">
  <h1>{{ job.tittle }}</h1>
  <p>this is job {{ id }}</p>
  <p>{{ job.details }}</p>
</div>
<div v-else>
  <p>Data Loging...</p>
</div>
</template>

<script>
export default {
    props:['id'],
    data() {
      return {
        job: null
      }
    },
    mounted() {
      fetch('http://localhost:3000/jobs/' + this.id)
        .then(res => res.json())
        .then(data => this.job = data)
        .catch(err => console.log(err.message))
    }
}
</script>

<style>

</style>