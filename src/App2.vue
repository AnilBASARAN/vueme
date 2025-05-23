<script>
  // with the options api you do have to export default
  // from the script so you have access to the data and methods 
  // in your template
export default {
  // THİS İS THE OPTİON
  data(){
    return {
      name:"John Doe",
      status: "yow yow",
      tasks: ["task one", "task two", "task three"],
      link: "https://google.com"
    };
  },
  methods: {
    toggleStatus(){
      if(this.status === "active"){
        this.status = "pending";
      }else if(this.status === "pending"){
        this.status = "inactive";
      }else{
        this.status = "active";
      }
    }
  }
};
</script>


<template>
<h1>{{ name }}</h1>
<p v-if="status === 'active' "> User is active </p>
<p v-else-if="status === 'pending'" >User is pending</p>
<p v-else >User is {{status}}</p>

<h3>Tasks:</h3>
<ul>
  <li v-for="task in tasks" :key="task">{{ task }}</li>
</ul>
<a v-bind:href="link">Click for google</a>
<br />
<button v-on:click="toggleStatus">Change Status</button>
<br />
<button  @click="toggleStatus"> this too Change Status</button>
</template>

<style scoped>
h1 {
  color: red;
}
</style>