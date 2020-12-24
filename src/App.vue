<template>
  <p class="debug">{{ debug }}</p>
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
          id: '404',
          name: 'I AM ERROR',
          date: '01/01/1970',
          avatar: '404.jpg',
          badges: [
            { name: 'Telepills', description: 'Tu avais 6.66% de chance (1/15) de finir ici !', date: '???', icon: 'telepills.jpg' }
          ]
        },
        {
          id: 'monsieurcro',
          name: 'MonsieurCro',
          date: '06/12/2020',
          avatar: 'monsieurcro.jpg',
          badges: [
            { name: 'Membre du Crollandais Volant', description: 'Le meilleur vaisseau, tout simplement.', date: '06/12/2020', icon: 'aworldofcro_black.jpg' },
            { name: 'A Wonderful Winter', description: 'A affronté le Grand Nord avec le capitaine.', date: '06/12/2020', icon: 'aworldofcro_normal.jpg' }
          ]
        },
        {
          id: 'test',
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
  .debug {
    position: absolute;
    left: 0; bottom: 0; right: auto; top: auto;
    font-size: 75%;
    font-style: italic;
    color: yellow;
  }
</style>