<template>
<div>
    <button type="button" class="btn btn-danger" v-on:click="background =!background">Change Color</button>

<table class="container">

  <thead>

    <tr>

      <th>Id</th>

      <th>Name</th>

      <th>UserName</th>

      <th>Email</th>

    </tr>

  </thead>
  <tbody v-for="(user,index) in users" :key="index">

    <tr v-if="user.id%2==0" class="text-white p-3" :class="{'bg-info' : background , 'bg-success' : !background}">
      <td>{{user.id}}</td>
      <td>{{user.name}}</td>
      <td>{{user.username}}</td>
      <td>{{user.email}}</td>
    </tr>
    <tr v-else class="text-white p-3" :class="{'bg-success' : background , 'bg-info' : !background}">
      <td>{{user.id}}</td>
      <td>{{user.name}}</td>
      <td>{{user.username}}</td>
      <td>{{user.email}}</td>
    </tr> 
  </tbody>
</table>
</div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      users: [],
      background: false, 
    }
  },
  created() {
    this.userList();
    
  },
  methods: {
    userList(){
      axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {console.log(response.data);
      this.users = response.data;})
    }  
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
