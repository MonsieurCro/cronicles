<template>
  <div class="fixed top right"><a @click.prevent.stop="showProfile">Profil</a></div>

  <div id="welcome" class="centered shadow blur">
    <div class="section horizontal">
      <img class="fit_image mobile" id="logo" src="assets/logo.png" alt="The Cronicles | Into the Unknown"/>
      <h1 class="title desktop">The Cronicles</h1>
      <h4 class="subtitle desktop">Into the Unknown</h4>
    </div>
    <div class="section horizontal">
      <div class="form">
        <div class="form_line">
          <label for="game">Accéder à l'aventure</label>
          <input id="game" class="blur" name="game" type="text" value="TEST_GAME" placeholder="" pattern="" title="" oninvalid="event.preventDefault();" disabled="disabled"/>
        </div>
        <div class="form_line">
          <button class="blur" type="submit" @click.prevent.stop="showGame">Démarrer</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'welcome',
    props: {},
    data() {
      return {
      }
    },
    methods: {
      showGame: function(){
        this.$emit('showGame', 1);
      },
      showProfile: function(){
        this.$emit('showProfile', 2);
      }
    },
    emits: ['showGame', 'showProfile'],
    computed: {}
  }
</script>

<style scoped>
  #welcome {
    height: 75%; max-height: 375px;
    width: 85%; max-width: 600px;
  }
  #welcome .title {
    font-size: 375%;
    margin: .025em auto;
  }
  #welcome .subtitle {
    font-size: 125%;
    margin: .0125em auto;
  }
</style>