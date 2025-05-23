<script setup>
//THİS İS THE COMPOSİTİON
import {ref,onMounted} from "vue";
// by default these values arent reactive, we need the status
//to be reactive because we want it to react to this button
//to fix that we need to wrap it in a function called ref
// there is also a function called reactive which you can use with
// objects
// we need to remove the keyword 'this' to status.value

  // we can write 'setup' in the script tag so we dont need to use it
  //also we dont need to export default it

    const name = ref("John Doe");
    const status =ref("active") ;
    const tasks = ref(["T1ask One","T1ask Two","T1ask Three"]) ;
    const newTask = ref("");
    // you can think of REF sort of a use state in react
    // because you can't just have a variable and than reassign it to
    //smth
    // you update it with use State
    // but vith vue you can just set the value with=> status.value
    const toggleStatus=()=>{
      if(status.value === "active"){
        status.value = "pending";
      }else if(status.value === "pending"){
        status.value = "inactive";
      }else{
        status.value = "active";
      }
    };

    const addTask =()=> {
      if(newTask.value.trim() !== "" ){
        tasks.value.push(newTask.value);
        newTask.value = "";
      }
    }

    const deleteTask =(index)=>{
      tasks.value.splice(index,1);
    }

    onMounted(async()=>{
      try{
        const response = await fetch("https://jsonplaceholder.typicode.com/todos");
        const data = await response.json();
        tasks.value = data.map((task)=> task.title);
      }catch(error){
        console.log("Error fetching tasks");
      }
    })
/*     return {
      name,
      status,
      tasks,
      toggleStatus,
    } */
// if we write setup in the script we dont need to explicitly return
</script>


<template>
<h1>{{ name }}</h1>
<p v-if="status === 'active' "> User is active </p>
<p v-else-if="status === 'pending'" >User is pending</p>
<p v-else >User is {{status}}</p>

<form @submit.prevent="addTask">
  <label for="newTask">Add Task</label>
  <input type="text" id="newTask" name="newTask" v-model="newTask" />
  <button type="submit" >SubMit</button>
</form>

<h3>Tasks:</h3>
<ul>
  <li v-for="(task,index) in tasks" :key="task">
    <span>
      {{ task }}
    </span>
    <button @click="deleteTask(index)" >X</button>
  </li>
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