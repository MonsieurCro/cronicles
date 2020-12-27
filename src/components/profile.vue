<template>
  <div class="fixed top right"><a @click.prevent.stop="showGame">Jeu</a></div>

  <div id="profile" class="centered shadow blur">
    <div class="section vertical">
      <img id="avatar" :src="publicPath + 'users/' + user.avatar"/><!-- :alt="user.name" -->
      <a :href="'https://www.dealabs.com/profile/' + user.name" target="_blank"><p class="title">{{ user.name }}</p></a>
      <p class="subtitle">A rejoint le {{ user.date }}</p>
      <div class="close" @click.prevent.stop="cleanUser">✕</div>
    </div>
    <div class="section vertical">
      <div class="badge" v-for="badge in user.badges" :key="badge">
        <img class="icon" :src="publicPath + 'badges/' + badge.icon"/><!-- :alt="badge.name" -->
        <div class="description">
          <p class="title">{{ badge.name }}</p>
          <p class="subtitle">{{ badge.description }} | {{ badge.date }}</p>
        </div>
      </div>
    </div>
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
      showGame: function(){
        this.$emit('showGame', 1);
      },
      cleanUser: function(){
        this.$emit('cleanUser');
      }
    },
    emits: {},
    computed: {}
  }
</script>

<style scoped></style>