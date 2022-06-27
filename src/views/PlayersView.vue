<template>
  <div class="players">
    <br>
   
      <h2 style="margin:20px; color: blue; text-align: center;">Players</h2>
      <b><p style="margin:20px; color: black; text-align: center;" v-if="show_counter">Found {{ total_count }} players</p></b>
    
      <v-text-field append-icon="mdi-magnify" placeholder="Enter players name or last name.." solo style="margin: 20px" v-model="pretraga" @change="dohvatiAPI()"></v-text-field>


    <v-containter>
      <v-row>
        <v-col cols="12" xl="3" lg="4" md="6" sm="12" xs="12" v-for="player in players" :key="player.id">
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
              
              <v-card-title class="justify-center">{{ player.first_name + ' ' + player.last_name}}</v-card-title>

              <v-card-text style="color: blue; text-align: center;">
                <div>Position: {{ player.position}}</div>
                <div>Height feet: {{ player.height_feet}}</div>
                <div>Height inches: {{ player.height_inches}}</div>
                <div>Weight pounds: {{ player.weight_pounds}}</div>
              </v-card-text>

              <v-divider class="mx-4"></v-divider>

              <v-card-title class="justify-center">{{ player.team.full_name}}</v-card-title>

            </v-card>-->

            <player-component :player="player" ></player-component>
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
import PlayerComponent from '@/components/Player.vue'


export default {
  components: { PlayerComponent },
  name: 'PlayersView',
   data: () => ({
    pretraga: '',
    loading: false,
    selection: 1,
    players: [],
    prikazi: false,
    total_pages: 151,
    current_page: 1,
    next_page: 2,
    per_page: 15,
    total_count: 3757,
    show_counter: false,
    
    
  }),
   methods: {
      dohvatiAPI: function(){
       this.axios.get('https://www.balldontlie.io/api/v1/players?search=' + this.pretraga + '&page=' + this.current_page + '&per_page=' + this.per_page).
       then((response) => {
          this.players = response.data.data
          this.pagination = response.data.meta
          this.prikazi = true
          this.total_pages = response.data.meta.total_pages
          this.current_page = response.data.meta.current_page
          this.next_page = response.data.meta.next_page
          //this.per_page = response.data.meta.per_page
          this.total_count = response.data.meta.total_count
          this.show_counter = true

          for(let i = 0; i < this.total_count; i++){
            if(this.players[i].position == "" ){
              this.players[i].position = 'Retired'
            }
          }

            for(let i = 0; i < this.players.length; i++){
            if((this.players[i].height_feet == null) || (this.players[i].height_inches == null) || (this.players[i].weight_pounds == null)){
              this.players[i].height_feet = 'Unmeasured'
              this.players[i].height_inches = 'Unmeasured'
              this.players[i].weight_pounds = 'Unmeasured'
            }
          }

  

         
          
        })
      },
    }
}
</script>
