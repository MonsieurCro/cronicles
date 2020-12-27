<template>
  <div class="fixed top right"><a @click.prevent.stop="showGame">Jeu</a></div>

  <div id="profile" class="centered shadow blur">
    <div class="section vertical">
      <img class="avatar" :src="publicPath + 'users/' + user.avatar"/><!-- :alt="user.name" -->
      <a :href="'https://www.dealabs.com/profile/' + user.name" target="_blank"><div class="title">{{ user.name }}</div></a>
      <div class="subtitle">A rejoint le {{ user.date }}</div>
    </div>
    <div class="section vertical">
      <div class="badge" v-for="badge in user.badges" :key="badge">
        <img class="icon" :src="publicPath + 'badges/' + badge.icon"/><!-- :alt="badge.name" -->
        <div class="description">
          <div class="title">{{ badge.name }}</div>
          <div class="subtitle">{{ badge.description }} | {{ badge.date }}</div>
        </div>
      </div>
    </div>
    <div class="close" @click.prevent.stop="cleanUser">✕</div>
  </div>
</template>

<script>
  export default {
    name: 'profile',
    props: {
      user: Object
    },
    data() {
      return {
        publicPath: process.env.BASE_URL + 'assets/'
      }
    },
    methods: {
      cleanUser: function(){
        this.$emit('cleanUser');
      },
      showGame: function(){
        this.$emit('showGame', 1);
      }
    },
    emits: {},
    computed: {}
  }
</script>

<style scoped>
  #profile {
    height: 80%; max-height: 500px;
    width: 85%; max-width: 1100px;
  }
  #profile .avatar {
    width: 5em; height: 5em;
    border-radius: 50%;
    margin: .75em .75em .5em;
    background-color: rgba(0, 0, 0, .15);
    overflow: hidden;
  }
  #profile .badge {
    width: 100%;
    text-align: left;
    padding: .25em .5em;
  }
  #profile .badge .icon {
    display: inline-block;
    height: 3em; width: 3em;
    vertical-align: middle;
    background-color: rgba(0, 0, 0, .15);
    overflow: hidden;
  }
  #profile .badge .description {
    display: inline-block;
    width: calc(100% - 3em);
    vertical-align: middle;
    padding-left: .5em;
  }
  #profile .badge .description * {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
</style>