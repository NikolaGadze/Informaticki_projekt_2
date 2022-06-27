<template>
  <div class="teams">
    <br>
   
      <h2 style="margin:20px; color: blue; text-align: center;">Teams</h2>
      <b><p style="margin:20px; color: black; text-align: center;">Currently in the NBA there are 30 teams, divided in 2 conferences and 6 divisions</p></b>
    
    <v-containter>
      <v-row>
        <v-col cols="12" xl="3" lg="4" md="6" sm="12" xs="12" v-for="team in teams" :key="team.id">
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

              <v-card-title class="justify-center">{{ team.full_name}}</v-card-title>
              
              <v-card-text style="color: blue; text-align: center;">
                <div>Conference: {{ team.conference }} </div>
                <div>Division: {{ team.division }} </div>
                <div>City: {{ team.city }}</div>
                <div>Brand name: {{ team.name }}</div>
                <div>Short: {{ team.abbreviation }}</div>
                <div>ID: {{ team.id }}</div>
              </v-card-text>
  
            </v-card>-->

            <team-component :team="team"></team-component>
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
import TeamComponent from '@/components/Team.vue'

export default {
  name: 'PlayersView',
  components: {TeamComponent},
   data: () => ({
    teams: [],
    prikazi: false,
    total_pages: 151,
    current_page: 1,
    next_page: 2,
    per_page: 15,
    total_count: 3757,
  
    
    
  }),
  mounted(){
    this.dohvatiAPI()
  },
   methods: {
      dohvatiAPI: function(){
       this.axios.get('https://www.balldontlie.io/api/v1/teams?'  + '&page=' + this.current_page + '&per_page=' + this.per_page).
       then((response) => {
          this.teams = response.data.data
          this.pagination = response.data.meta
          this.prikazi = true
          this.total_pages = response.data.meta.total_pages
          this.current_page = response.data.meta.current_page
          this.next_page = response.data.meta.next_page
          //this.per_page = response.data.meta.per_page
          this.total_count = response.data.meta.total_count



        })
      },
    }
}
</script>
