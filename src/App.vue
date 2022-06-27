<template>
  <v-app id="inspire">
    <v-app-bar
      app
      color="indigo darken-2"
      flat
    > 
     
      <v-tabs
        centered
        class="ml-n9"
        color="white darken-1"
      >
        <v-tab
          v-for="link in links"
          :key="link"
          :to="link.ruta"
        >
          {{ link.ime }}
        </v-tab>
      </v-tabs>


    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            sm="12">
            <v-sheet
              min-height="100vh"
              rounded="lg">
              <router-view/>
            </v-sheet>
          </v-col>

         
        </v-row>
      </v-container>
    </v-main>

      
      

      <v-bottom-navigation>
        <v-btn @click="toFacebook()">
          <v-icon color="indigo darken-2" >mdi-facebook</v-icon>
        </v-btn>

        <v-btn @click="toInstagram()">
          <v-icon color="pink accent-3">mdi-instagram</v-icon>
        </v-btn>

        <v-btn @click="toTwitter()">
          <v-icon color="cyan lighten-2">mdi-twitter</v-icon>
        </v-btn>

        <v-btn @click="toYouTube()">
          <v-icon color="red darken-1">mdi-youtube</v-icon>
        </v-btn>

        <v-btn @click="toTwitch()">
          <v-icon color="deep-purple lighten-2">mdi-discord</v-icon>
        </v-btn>
        
        

      </v-bottom-navigation>
    


  </v-app>
</template>

<script>
  export default {
    data: () => ({
      naslov: document.title = 'NBA',
      links: [
        {ime: 'Home', ruta: '/'},
        {ime: 'Players', ruta: '/players'},
        {ime: 'Teams', ruta: '/teams'},
        {ime: 'Games', ruta: '/games'},
        {ime: 'About', ruta: '/about'}
      ],
      icons: [
        'mdi-facebook',
        'mdi-instagram',
        'mdi-twitter',
        'mdi-youtube',
        'mdi-twitch'
      ],
    }),
    methods: {
      toFacebook: function(){
        window.open('https://www.facebook.com/nba')
      },
       toInstagram: function(){
        window.open('https://www.instagram.com/accounts/login/?next=/nba/')
      },
       toTwitter: function(){
        window.open('https://twitter.com/NBA')
      },
       toYouTube: function(){
        window.open('https://www.youtube.com/user/NBA')
      },
       toTwitch: function(){
        window.open('https://www.twitch.tv/nba')
      },
    }
  }
</script>