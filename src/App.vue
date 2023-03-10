<template>
  <div id="app">
    <WaitSpinner v-if="showLoading" />
    <AddForm v-else v-on:addUser="addUser" />
    <UserCard v-bind:allUsers="users" msg="my message" />
    <button v-on:click="handleToggle">Toggle</button>
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
  data: function () {
    return {
      users: [],
      showLoading: true,
    }
  },
  methods: {
    addUser: function (newUser) {
      console.log("called", newUser);
      this.users.push(newUser);
    },
    handleToggle: function () {
      // console.log("clicked");
      this.showLoading = !this.showLoading
    }
  },
  mounted() {
    console.log("app monted");
    setTimeout(function () {
      this.showLoading = false;
      // console.log(this.showLoading);
      // console.log("after 2 seconds");
    }, 2000)
  },
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
