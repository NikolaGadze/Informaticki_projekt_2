<template>
  <div class="games">
    <br>
   
      <h2 style="margin:20px; color: blue; text-align: center;">Games</h2>

      <h3 style="margin:20px; text-align: center;">Here you see all games of a selected team, for the entered season</h3>

      <v-autocomplete label="Select the team.." style="margin: 20px"  solo :items="teams" v-model="team"></v-autocomplete>
    
      <v-text-field append-icon="mdi-magnify" placeholder="Enter the season.." solo style="margin: 20px" v-model="pretraga" @keyup.enter="dohvatiAPI()"></v-text-field>

    <v-containter>
      <v-row>
        <v-col cols="12" xl="3" lg="4" md="6" sm="12" xs="12" v-for="game in games" :key="game.id">
             <!--<v-card
              :loading="loading"
              class="mx-auto my-12"
              max-width="350"
            >
              <template slot="progress">
                <v-progress-linear
                  color="deep-purple"
                  height="10"
                  indeterminate
                ></v-progress-linear>
              </template>

              <v-card-title style="color: blue" class="justify-center">{{ game.home_team.name + ' ' + game.home_team_score +  ' : ' + game.visitor_team_score + ' ' + game.visitor_team.name}}</v-card-title>
      
              <v-divider class="mx-4"></v-divider>

              <v-card-title class="justify-center"> {{ game.postseason}}</v-card-title>
              <v-card-title class="justify-center">Season: {{ game.season}}</v-card-title>
              <v-card-title class="justify-center">Status: {{ game.status}}</v-card-title>
              <v-card-title class="justify-center">Period: {{ game.period}}</v-card-title>
              <v-card-title class="justify-center">Time: {{ game.time}}</v-card-title>

              <v-divider class="mx-4"></v-divider>
              <v-card-title class="justify-center"><b>Date: </b> {{ game.date }}</v-card-title>

            </v-card>-->

            <game-component :game="game"></game-component>
        </v-col>
      </v-row>
    </v-containter>

      <div class="text-center" v-if="prikazi" @click="dohvatiAPI()">
        <v-pagination
          v-model="current_page"
          :length="total_pages"
          total-visible="9"
          prev-icon="mdi-menu-left"
          next-icon="mdi-menu-right"
        ></v-pagination>
      </div>
  </div>
</template>

<script>
import GameComponent from '@/components/Game.vue'

export default {
  name: 'PlayersView',
  components: {GameComponent},
   data: () => ({
    pretraga: '',
    loading: false,
    selection: 1,
    games: [],
    prikazi: false,
    total_pages: 151,
    current_page: 1,
    next_page: 2,
    per_page: 15,
    total_count: 3757,
    team: '',
    teams: [
      {value: 1, text: 'Atlanta Hawks'},
      {value: 2, text: 'Boston Celtics'},
      {value: 3, text: 'Brooklyn Nets'},
      {value: 4, text: 'Charlotte Hornets'},
      {value: 5, text: 'Chicago Bulls'},
      {value: 6, text: 'Cleveland Cavaliers'},
      {value: 7, text: 'Dallas Mavericks'},
      {value: 8, text: 'Denver Nuggets'},
      {value: 9, text: 'Detroit Pistons'},
      {value: 10, text: 'Golden State Warriors'},
      {value: 11, text: 'Houston Rockets'},
      {value: 12, text: 'Indiana Pacers'},
      {value: 13, text: 'LA Clippers'},
      {value: 14, text: 'Los Angeles Lakers'},
      {value: 15, text: 'Memphis Grizzlies'},
      {value: 16, text: 'Miami Heat'},
      {value: 17, text: 'Milwaukee Bucks'},
      {value: 18, text: 'Minnesota Timberwolves'},
      {value: 19, text: 'New Orleans Pelicans'},
      {value: 20, text: 'New York Knicks'},
      {value: 21, text: 'Oklahoma City Thunder'},
      {value: 22, text: 'Orlando Magic'},
      {value: 23, text: 'Philadelphia 76ers'},
      {value: 24, text: 'Phoenix Suns'},
      {value: 25, text: 'Portland Trail Blazers'},
      {value: 26, text: 'Sacramento Kings'},
      {value: 27, text: 'San Antonio Spurs'},
      {value: 28, text: 'Toronto Raptors'},
      {value: 29, text: 'Utah Jazz'},
      {value: 30, text: 'Washington Wizards'}
    ]

    
    
    
  }),
   methods: {
      dohvatiAPI: function(){
       this.axios.get('https://www.balldontlie.io/api/v1/games?seasons[]=' + this.pretraga + '&team_ids[]=' + this.team + '&page=' + this.current_page + '&per_page=' + this.per_page).
       then((response) => {
          this.games = response.data.data
          this.pagination = response.data.meta
          this.prikazi = true
          this.total_pages = response.data.meta.total_pages
          this.current_page = response.data.meta.current_page
          this.next_page = response.data.meta.next_page
          //this.per_page = response.data.meta.per_page
          this.total_count = response.data.meta.total_count


           for(let i = 0; i < this.games.length; i++){
            if(this.games[i].postseason == false){
              this.games[i].postseason = 'Regular season'
            } else {
              this.games[i].postseason = 'Play-off'
            }
          }

           for(let i = 0; i < this.games.length; i++){
            if(this.games[i].status == 'Final'){
              this.games[i].time = '00:00'
            } 
          }
          
        })
      },
    }
}
</script>
