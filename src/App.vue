<template>
  <welcome
  v-if="appScreen === 0"
  @showGame="switchStep" @showProfile="switchStep">
  </welcome>
  <game
  v-if="appScreen === 1"
  @showProfile="switchStep">
  </game>
  <login
  v-if="appScreen === 2 && loginForm.completed === false"
  v-bind:login="loginForm"
  @formSubmit="formCompleted" @showGame="switchStep">
  </login>
  <profile
  v-if="appScreen === 2 && loginForm.completed"
  v-bind:user="currentUser"
  @cleanUser="resetUser" @showGame="switchStep">
  </profile>
  <div class="debug">{{ debug }}</div>
</template>

<script>
  import welcome from './components/welcome.vue'
  import game from './components/game.vue'
  import login from './components/login.vue'
  import profile from './components/profile.vue'

  export default {
    name: 'VueApp',
    components: {
      welcome,
      game,
      login,
      profile
    },
    data() {
      return {
        appScreen: 0,
        loginForm: {
          completed: false,
          user: ''
        },
        currentUser: {},
        playersList: [
        {
          id: '404',
          name: 'I AM ERROR',
          date: '01/01/1970',
          avatar: '404.jpg',
          badges: [0]
        },
        {
          id: 'monsieurcro',
          name: 'MonsieurCro',
          date: '16/11/2020',
          avatar: 'monsieurcro.jpg',
          badges: [1,2]
        },
        {
          id: 'joldman',
          name: 'J.Oldman',
          date: '16/11/2020',
          avatar: 'joldman.jpg',
          badges: [1,2]
        },
        {
          id: 'natito',
          name: 'Natito',
          date: '16/11/2020',
          avatar: 'natito.jpg',
          badges: [1,2]
        },
        {
          id: 'tontonfraguer',
          name: 'tontonfraguer',
          date: '16/11/2020',
          avatar: 'tontonfraguer.jpg',
          badges: [2,3]
        },
        {
          id: 'jomi',
          name: 'jo_mi',
          date: '16/11/2020',
          avatar: 'jomi.jpg',
          badges: [2,3]
        },
        {
          id: 'worazme',
          name: 'Worazme',
          date: '16/11/2020',
          avatar: 'worazme.jpg',
          badges: [2,3]
        },
        {
          id: 'lozen',
          name: 'Lozen',
          date: '16/11/2020',
          avatar: 'lozen.jpg',
          badges: [2]
        },
        {
          id: 'tucsoufle',
          name: 'Tucsoufle',
          date: '16/11/2020',
          avatar: 'tucsoufle.jpg',
          badges: [2]
        },
        {
          id: 'darksareth',
          name: 'darksareth',
          date: '16/11/2020',
          avatar: 'darksareth.jpg',
          badges: [2]
        },
        {
          id: 'flightfire1',
          name: 'flightfire1',
          date: '16/11/2020',
          avatar: 'flightfire1.jpg',
          badges: [2,4]
        },
        {
          id: 'rhezor',
          name: 'Rezhor',
          date: '16/11/2020',
          avatar: 'rezhor.jpg',
          badges: [2,4]
        },
        {
          id: 'devezeemm',
          name: 'deveze_emm',
          date: '16/11/2020',
          avatar: 'devezeemm.jpg',
          badges: [2,4]
        },
        {
          id: 'babysylvie',
          name: 'BabySylvie',
          date: '16/11/2020',
          avatar: 'babysylvie.jpg',
          badges: [2,5]
        },
        {
          id: 'demiss',
          name: 'Demiss',
          date: '16/11/2020',
          avatar: 'demiss.jpg',
          badges: [2,5]
        },
        {
          id: 'ptitchoco',
          name: 'PtitChoco',
          date: '16/11/2020',
          avatar: 'ptitchoco.jpg',
          badges: [2,5]
        },
        {
          id: 'freddo935',
          name: 'freddo935',
          date: '16/11/2020',
          avatar: 'freddo935.jpg',
          badges: [2]
        },
        {
          id: 'chocoloustic',
          name: 'Chocoloustic',
          date: '16/11/2020',
          avatar: 'chocoloustic.jpg',
          badges: [2]
        },
        {
          id: 'makou',
          name: 'makou',
          date: '16/11/2020',
          avatar: 'makou.jpg',
          badges: [2]
        },
        {
          id: 'nelson34',
          name: 'Nelson34',
          date: '16/11/2020',
          avatar: 'nelson34.jpg',
          badges: [2]
        },
        {
          id: 'dragonfly59',
          name: 'dragonfly59',
          date: '16/11/2020',
          avatar: 'dragonfly59.jpg',
          badges: [2]
        },
        {
          id: 'psyko5457',
          name: 'Psyko5457',
          date: '16/11/2020',
          avatar: 'psyko5457.jpg',
          badges: [2]
        }
        ],
        badgesList: [
        { id: 0, name: 'Telepills 💊', description: 'Tu avais 6.66% de chance (1/15) de finir ici !', date: '???', icon: 'telepills.jpg' },
        { id: 1, name: 'Membre du Crollandais Volant ☠️', description: 'Le meilleur vaisseau, tout simplement.', date: '16/11/2020', icon: 'aworldofcro_black.jpg' },
        { id: 2, name: 'A Wonderful Winter 🏅', description: 'A bravé le Grand Nord...', date: '07/12/2020', icon: 'aworldofcro_normal.jpg' },
        { id: 3, name: 'A Wonderful Winter 🥇', description: '...et est reparti avec le trésor !', date: '07/12/2020', icon: 'aworldofcro_gold.jpg' },
        { id: 4, name: 'A Wonderful Winter 🥈', description: '...et a failli gagner !', date: '07/12/2020', icon: 'aworldofcro_silver.jpg' },
        { id: 5, name: 'A Wonderful Winter 🥉', description: '...et y a laissé un orteil !', date: '07/12/2020', icon: 'aworldofcro_bronze.jpg' }
        ]
      }
    },
    methods: {
      switchStep: function(step){
        console.log('switch')
        this.appScreen = step;
      },
      formCompleted: function(user){
        this.loginForm.user = user.toLowerCase().replace(/[^a-zA-Z0-9]+/g, '');
        this.loginForm.completed = true;

        this.playersList.forEach(this.findUser);
        if(!this.currentUser.id){
          this.currentUser = this.playersList[0];
          console.warn('Vue | App | User not found');
        }

        this.currentUser.badges.forEach(this.renderBadges);
      },
      findUser: function(user){
        if(user.id === this.loginForm.user){
          this.currentUser = user;
        }
      },
      renderBadges: function(badge, index){
        for(var i = 0; i < this.badgesList.length; i++){
          if(this.badgesList[i].id === badge){
            this.currentUser.badges[index] = this.badgesList[i];
          }
        }
        if(!this.currentUser.badges[index].name){
          this.currentUser.badges[index] = this.badgesList[0];
          console.warn('Vue | App | Badge not found');
        }
      },
      resetUser: function(){
        this.currentUser = '';
        this.loginForm.user = '';
        this.loginForm.completed = false;
      }
    },
    computed: {
      debug: function(){
        var data = ''; //'Step: ' + this.appScreen;
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
    left: .5em; bottom: .5em; right: auto; top: auto;
    font-size: 75%;
    font-style: italic;
    color: yellow;
    background-color: rgba(0, 0, 0, .25);
    padding: .25em;
    z-index: 9999;
  }
</style>