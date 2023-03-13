<template>
    <div class="component-one">
        <form v-on:submit.prevent="handleAddUser" action="" class="form">
            <label for="name">Name :
                <input type="text" v-model="name" placeholder="Your name...">
            </label>
            <label for="age">Age :
                <input type="text" v-model="age" placeholder="Your age...">
            </label>
            <label for="role">Role :
                <input type="text" v-model="role" placeholder="Your role...">
            </label>
            <button class="button" type="submit">Add</button>
        </form>
        <button class="openbtn" v-on:click="openModal">Open Modal</button>
        <button v-on:click="test">Harlin</button>
    </div>
</template>
<script>
export default {
    name: 'AddForm',
    props: ['test'],
    data: function () {
        return {
            name: '',
            age: '',
            role: '',
        }
    },
    methods: {
        handleAddUser() {
            this.$emit('addUser',{name:this.name, age:this.age, role:this.role})
        },
        openModal(){
            this.$emit('showModal')
        },
        testKely() {
            // this.test = 'Harlin Davidson'
        }
    },
}
</script>
<style>
.button {
    width: 150px;
    align-items: center;
    margin: auto;
}

.component-one {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 300px;
}

.form {
    display: flex;
    flex-direction: column;
    width: 100%;
    gap: 20px;
}
</style>