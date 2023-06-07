<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>The job id is {{ id }}</p>
    <p>{{ job.detail }}</p>
  </div>
  <div v-else>
    <p>Loading job details ... </p>
  </div>
</template>

<script>
  export default {
    // to get the id, either use this.$route.params.id or you can accept it as props
    props: [ 'id' ],
    data() {
      return {
        job: null
      }
    },
    mounted() {
      fetch(`http://localhost:3000/jobs/${this.id}`)
        .then((res) => res.json())
        .then((data) => this.job = data)
        .catch(console.error)
    }
  }
</script>

<style>

</style>