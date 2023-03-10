<template>
  <div id="app">
    <AddForm v-on:addUser="addUser"/>
    <UserCard v-bind:allUsers="users" msg="my message"/>
    <WaitSpinner/>
  </div>
</template>

<script>
import AddForm from './components/AddForm.vue'
import UserCard from './components/UserCard.vue'
import WaitSpinner from './components/WaitSpinner.vue'

export default {
  name: 'App',
  components: {
    AddForm, UserCard, WaitSpinner
  },
  data: function() {
    return {
      users: []
    }
  },
  methods: {
    addUser:function(newUser) {
      console.log("called", newUser);
      this.users.push(newUser);
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
