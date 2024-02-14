<template>
    <div>
        <h1> Registrace </h1>
        <form @submit.prevent="submitForm">
            <div class="form-group">
                <label for class=""> uživatelské jméno </label>
                <input type="text" name="username" class="">
            </div> 
            <div class="form-group">
                <label for> heslo </label>
                <input type="password" name="password">
            </div>
            <div class="form-group">
                <label for> heslo znovu </label>
                <input type="password" name="password">
            </div> 
            <button type="submit"> registrovat se </button>
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
}
</script>

<style>

</style>