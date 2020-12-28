<template>
  <div class="fixed top right"><a @click.prevent.stop="showGame">Jeu</a></div>

  <div id="players" class="centered shadow blur">
    <div class="section full">
      <div class="user" v-for="user in cleanUserList" :key="user" @click.prevent.stop="playerSelected(user.name)">
        <div class="title">{{ user.name }}</div>
      </div>
    </div>
    <div class="close" @click.prevent.stop="hideList">✕</div>
  </div>
</template>

<script>
  export default {
    name: 'players',
    props: {
      users: Object
    },
    data() {
      return {
        publicPath: process.env.BASE_URL + 'assets/'
      }
    },
    methods: {
      playerSelected: function(user){
        this.$emit('playerSelected', user);
      },
      hideList: function(){
        this.$emit('hideList');
      },
      showGame: function(){
        this.$emit('showGame', 1);
      }
    },
    emits: ['playerSelected', 'hideList', 'showGame'],
    computed: {
      cleanUserList: function(){
        return this.users.filter(function(item, index){
          return index > 0;
        }).sort(function(a, b){
          if(a.id < b.id) { return -1; }
          if(a.id > b.id) { return 1;  }
          return 0;
        });
      }
    }
  }
</script>

<style scoped>
  #players {
    height: 80%; max-height: 500px;
    width: 85%; max-width: 1100px;
  }
  #players .section {
    display: block;
  }
  #players .user {
    height: auto; width: 100%;
    padding: .25em .5em;
    text-align: left;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    flex-direction: row;
  }
  #players .user * {
    display: inline-block;
  }
  #players .user .avatar {
    height: 3em; width: 3em;
    margin: 0;
    border-radius: 50%;
    background-color: rgba(0, 0, 0, .15);
    overflow: hidden;
  }
</style>