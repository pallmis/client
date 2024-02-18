<template>
    <div>
        <h1> Přihlásit se </h1>
        <form @submit.prevent="submitForm">
            <div class="form-group">
                <label for class=""> uživatelské jméno </label>
                <input type="text" name="username" class="">
            </div> 
            <div class="form-group">
                <label for> heslo </label>
                <input type="password" name="password">
            </div> 
            <button type="submit"> přihlásit se </button>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    head() {
      return {
        title: "přihlášení"
      };
    }, 
    data() {
        return {
            username: '',
            password: '',
        }
    },
    methods: {
        async submitForm() {
            try {
                const response = await axios.post('/recipes/login/', {  // Django request 
                    username: this.username,
                    password: this.password,
                });
                console.log(response.data);
                this.$router.push('/recipes/'); // udělat stránku uživatele, změnit /recipes/ na /recipes/user/
          } catch (error) {
                console.error(error);
            }
        },
    },
}
</script>

<style>

form {
    display: flex;
    flex-direction: column;
    align-items: center;
}

.form-group {
    display: flex;
    flex-direction: row;
    justify-content: space-between; 
    align-items: center; 
    width: 40%;
}

label {
    display: block;
    text-align: left;
}

input {
    width: 50%; 
}

button {
    cursor: pointer;
}

</style>