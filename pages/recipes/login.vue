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
        submitForm() {
            
        }
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