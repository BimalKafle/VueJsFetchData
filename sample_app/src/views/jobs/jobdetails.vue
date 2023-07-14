<template>
  
    <div v-if="job">
            Job detail Page
    <h1>{{job.title}}</h1>
    <p>THe job id is {{id}}</p>
    <p>{{job.details}}</p>
    </div>
    <div v-else>
        <p>Loading data</p>
    </div>
  
</template>

<script>
export default {
data(){
    return{
        id:this.$route.params.id,
        job:null
    }
},
mounted(){
    fetch('http://localhost:3000/jobs/'+this.id)
    .then(res=>res.json())
    .then(data=>this.job=data)
    .catch(err=>console.log(err.message));
}
}
</script>

<style>

</style>