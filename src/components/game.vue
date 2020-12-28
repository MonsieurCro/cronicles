<template>
  <div class="fixed top right"><a @click.prevent.stop="showProfile">Profil</a></div>

  <div id="game" class="centered shadow blur">
    <div class="section full">
      <p>NOT YET!</p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'game',
    props: {},
    data() {
      return {
        publicPath: process.env.BASE_URL + 'assets/'
      }
    },
    methods: {
      showProfile: function(){
        this.$emit('showProfile', 2);
      }
    },
    emits: ['showProfile'],
    computed: {}
  }
</script>

<style scoped>
  #game {
    height: 80%; max-height: 500px;
    width: 85%; max-width: 1100px;
  }
</style>