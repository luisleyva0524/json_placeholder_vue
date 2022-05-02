<template>
  <h3>Json placeholder API USERS</h3>
  <table id="customers">
    <thead>
      <tr>
        <th>ID</th>
        <th>NAME</th>
        <th>USERNAME</th>
      </tr>
    </thead>
    <tbody v-for="user in users" :key="user.id">
      <tr>
        <td>{{ user.id }}</td>
        <td>{{ user.name }}</td>
        <td>{{ user.username }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data() {
    return {
      users: []
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/users').then((response) => {
      return response.json();
    }).then((user) => {
      this.users.push(...user);
      console.log(this.users);
    }).catch((error) => {
      console.log(error);
    });
  }
};
</script>

<style scoped>
h3 {
  text-align: center;
}

table {
  width: 100%;
  box-shadow: 1px 1px 1px 1px rgb(182, 180, 180);
}

th {
  background-color: rgb(96, 138, 158);
  text-align: center;
}

#customers tr:hover {
  background-color: #ddd;
}

tbody td{
  padding: 6px;
  border-top: 1px solid #ddd;
  border-collapse: separate;
}
</style>
