<template>
  <div id="login" class="centered shadow blur">
    <div class="section horizontal">
      <img class="fit_image mobile" id="logo" src="assets/logo.png" alt="The Cronicles | Into the Unknown"/>
      <h1 class="title desktop">The Cronicles</h1>
      <h4 class="subtitle desktop">Into the Unknown</h4>
    </div>
    <div class="section horizontal">
      <form class="form" @submit.prevent.stop="formSubmit">
        <div class="form_line">
          <label for="user">Entrez le pseudo recherché</label>
          <input id="user" class="blur" name="user" type="text" placeholder="" pattern="[a-zA-Z0-9_.-]{3,}" required="required" v-model="input_user" :disabled="login.completed === true"/>
        </div>
        <div class="form_line">
          <button class="blur" id="submit" type="submit" :disabled="login.completed === true">Espionner</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'login',
    props: {
      login: Object
    },
    data() {
      return {
        input_user: this.login.user
      }
    },
    methods: {
      formSubmit: function(){
        if(this.input_user && this.input_user != ''){
          this.$emit('formSubmit', this.input_user);
        } else {
          console.warn('Vue | Login Component | No user');
        }
      }
    },
    computed: {}
  }
</script>

<style scoped></style>