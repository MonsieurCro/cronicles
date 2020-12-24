<template>
  <p>{{ debug }}</p>
  <login v-bind:login="loginForm" @formSubmit="formCompleted" v-if="loginForm.completed === false"></login>
  <profile v-bind:user="currentUser" v-if="loginForm.completed"></profile>
</template>

<script>
import login from './components/login.vue'
import profile from './components/profile.vue'
export default {
  name: 'VueApp',
  components: {
    login,
    profile
  },
  data() {
    return {
      loginForm: {
        completed: false,
        user: ''
      },
      currentUser: {},
      listPlayers: [
        {
          id: 'monsieurcro',
          name: 'MonsieurCro',
          date: '01/01/1970',
          avatar: 'https://static-pepper.dealabs.com/users/user_avatar/default/83534_28.jpg',
          badges: [
            { name: 'Membre du Crollandais Volant', description: 'Le meilleur vaisseau, tout simplement.', date: '06/12/2020', icon: 'https://static-pepper.dealabs.com/users/user_avatar/default/83534_28.jpg' },
            { name: 'Test V-FOR', description: 'x', date: 'y', icon: 'z' },
            { name: 'Test V-FOR', description: 'x', date: 'y', icon: 'z' }
          ]
        },
        {
          id: 'logan',
          name: '',
          date: '',
          avatar: '',
          badges: [
            { name: '', description: '', date: '', icon: '' }
          ]
        }
      ]
    }
  },
  methods: {
    formCompleted: function(user){
      this.loginForm.user = user.trim().toLowerCase();
      this.loginForm.completed = true;

      this.listPlayers.forEach(this.findUser);
      if(!this.currentUser.id){
        this.currentUser = this.listPlayers[0];
      }
    },
    findUser: function(user){
      if(user.id == this.loginForm.user){
        this.currentUser = user;
      }
    }
  },
  computed: {
    debug: function(){
      var data = ''; //this.loginForm.user;
      return data;
    }
  }
}
</script>

<style>
  #app {
    width: 100%; height: 100%;
    position: absolute;
    top: 0; left: 0; bottom: 0; right: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>