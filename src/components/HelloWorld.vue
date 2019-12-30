<template>
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
    <tr v-if="user.id%2==0"  bgcolor="#00aae4">
      <td>{{user.id}}</td>
      <td>{{user.name}}</td>
      <td>{{user.username}}</td>
      <td>{{user.email}}</td>
    </tr>
    <tr v-else bgcolor="#ff0080">
      <td>{{user.id}}</td>
      <td>{{user.name}}</td>
      <td>{{user.username}}</td>
      <td>{{user.email}}</td>
    </tr>
  </tbody>

</table>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      users: []
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
