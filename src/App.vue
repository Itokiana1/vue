<template>
  <div id="app">
    <WaitSpinner v-if="showLoading" />
    <UserCard v-if="!showLoading" v-bind:allUsers="users" msg="my message" />
    <AddForm v-if="!showLoading" v-on:addUser="addUser" v-on:showModal="handleOpenModal" :test="test"/>
    <button v-if="!showLoading" v-on:click="handleToggle">Toggle</button>
    <ModalForm v-if="showModal" v-on:closeModal="handleCloseModal"/>
  </div>
</template>

<script>
import AddForm from './components/AddForm.vue'
import UserCard from './components/UserCard.vue'
import WaitSpinner from './components/WaitSpinner.vue'
import ModalForm from './components/ModalForm.vue'

export default {
  name: 'App',
  components: {
    AddForm, UserCard, WaitSpinner, ModalForm
  },
  data: function () {
    return {
      users: [],
      showLoading: true,
      showModal: false,
      closeModal:false,
      test: '',
    }
  },
  methods: {
    addUser: function (newUser) {
      console.log("called", newUser);
      this.users.push(newUser);
    },
    handleToggle() {
      // console.log("clicked");
      this.showLoading = !this.showLoading
    },
    handleOpenModal() {
      // console.log("open");
      this.showModal = !this.showModal
    },
    handleCloseModal () {
      // console.log("closed");
      this.showModal = !this.showModal
    }
  },
  mounted() {
    // console.log("app mounted");
    setTimeout(
      // console.log("after 2 sec");
      this.handleToggle, 2000)
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
