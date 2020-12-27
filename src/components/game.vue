<template>
  <div class="fixed top right"><a @click.prevent.stop="showProfile">Profil</a></div>

  <div id="game" class="centered shadow blur">
    <p>TODO</p>
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
    emits: {},
    computed: {}
  }
</script>

<style scoped></style>