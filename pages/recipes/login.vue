<template>
    <div>
        <h1> Přihlásit se </h1>
        <form @submit.prevent="submitForm">
            <div class="form-group">
                <label for> uživatelské jméno </label>
                <input type="text" name="username">
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

</style>