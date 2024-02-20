<script lang="ts">
  import JSONDATA from './MOCK_DATA.json'
  export default {
    name: 'search-filter',
    data() {
      return {
        users: JSONDATA,
        query: ''
      }
    },
    computed: {
      filteredUsers() {
        return this.users.filter(u => u.first_name.toLowerCase().includes(this.query.toLowerCase()))
      }
    }
  }
</script>

<template>
  <div class="app">
    <input type="text" placeholder="search..." v-model="query" />
    <div v-for="user in filteredUsers">
      <p>{{ user.first_name }}</p>
    </div>
  </div>
</template>

<style>
  .app {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: Arial, Helvetica, sans-serif;
  }

  input {
    margin: 15px 0;
    width: 280px;
    height: 40px;
    padding-left: 10px;
    font-size: 20px;
  }

  p {
    margin: 10px;
    font-size: 18px;
  }
</style>
