<template>
    <div>
      <section>
        <div>
          <div>
            <h1>Get GitHub Repositories</h1>
            <h2>using Vue JS &amp; REST API</h2>
          </div>
        </div>
      </section>
      <div class="container">
        <div class="table-container">
          <table>
            <thead>
              <tr>
                <th>ID</th>
                <th>Name</th>
                <th>URL</th>
                <th>Language</th>
                <th>Login</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="repo in repos" v-bind:key="repo.id">
                <td>{{ repo.id }}</td>
                <td>{{ repo.name }}</td>
                <td>{{ repo.html_url }}</td>
                <td>{{ repo.language }}</td>
                <td>{{ repo.owner.login }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  export default {
    name: "github-repository",
    data() {
      return {
        repos: null,
      };
    },
    created: function () {
      axios.get("https://api.github.com/users/baddamin-code/repos").then((response) => {
        this.repos = response.data;
      });
    },
  };
  </script>
  
  <style>
  body {
    font: 15px/1.8 "Poppins", sans-serif !important;
  }
  .table td,
  .table th {
    padding: 20px !important;
  }
  </style>