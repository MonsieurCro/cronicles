<template>
  <div class="fixed top right"><a @click.prevent.stop="showProfile">Profil</a></div>

  <div id="login" class="centered shadow blur">
    <div class="section horizontal">
      <img class="fit_image mobile" id="logo" src="assets/logo.png" alt="The Cronicles | Into the Unknown"/>
      <h1 class="title desktop">The Cronicles</h1>
      <h4 class="subtitle desktop">Into the Unknown</h4>
    </div>
    <div class="section horizontal">
      <div class="form">
        <div class="form_line">
          <label>Accéder au jeu</label>
          <button class="blur" type="submit" @click.prevent.stop="showGame">Lancer</button>
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
    emits: {},
    computed: {}
  }
</script>

<style scoped></style>