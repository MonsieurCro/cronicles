<template>
  <div class="fixed top right"><a @click.prevent.stop="showGame">Jeu</a></div>

  <div id="login" class="centered shadow blur">
    <div class="section horizontal">
      <img class="fit_image mobile" id="logo" src="assets/logo.png" alt="The Cronicles | Into the Unknown"/>
      <h1 class="title desktop">The Cronicles</h1>
      <h4 class="subtitle desktop">Into the Unknown</h4>
    </div>
    <div class="section horizontal">
      <form class="form" @submit.prevent.stop="formSubmit">
        <div class="form_line">
          <label for="user">Entrer un pseudo ou afficher la liste</label>
          <input id="user" class="blur" name="user" type="text" placeholder="" title="" oninvalid="event.preventDefault();" v-model="input_user" :disabled="login.user != ''"/><!-- pattern="[a-zA-Z0-9_.- ]{1,}" required="required" -->
        </div>
        <div class="form_line">
          <button class="blur" id="submit" type="submit" :disabled="login.user != ''">{{ buttonMessage }}</button>
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
        if(this.input_user && this.input_user.trim() != ''){
          this.$emit('formSubmit', this.input_user);
        } else {
          this.$emit('formSkipped');
        }
      },
      showGame: function(){
        this.$emit('showGame', 1);
      }
    },
    emits: ['formSubmit', 'formSkipped', 'showGame'],
    computed: {
      buttonMessage: function(){
        if(this.input_user.trim() != ''){
          return 'Espionner'
        } else {
          return 'Visualiser'
        }
      },
    }
  }
</script>

<style scoped>
  #login {
    height: 75%; max-height: 375px;
    width: 85%; max-width: 600px;
  }
  #login .title {
    font-size: 375%;
    margin: .025em auto;
  }
  #login .subtitle {
    font-size: 125%;
    margin: .0125em auto;
  }
</style>