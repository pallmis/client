<template>
    <div>
        <h1> Registrace </h1>
        <form @submit.prevent="submitForm">
            <div class="form-group">
                <label for class=""> uživatelské jméno </label>
                <input type="text" v-model="username">
            </div> 
            <div class="form-group">
                <label for> heslo </label>
                <input type="password" v-model="password">
            </div>
            <div class="form-group">
                <label for> heslo znovu </label>
                <input type="password" v-model="password2">
            </div> 
            <button type="submit"> registrovat se </button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    head() {
      return {
        title: "registrace"
      };
    },
    data() {
        return {
            username: '',
            password: '',
            password2: '',  
        };
    },
    methods: {
        async submitForm() {
            try {
                const response = await axios.post('http://localhost:8000/dlouhodobka/user/register/', {   // Django request
                    username: this.username,
                    password: this.password,
                    password2: this.password2,
                });
            console.log(response.data);
          } catch (error) {
                console.error(error);
            }
        },
    }, 
}
</script>

<style>

</style>