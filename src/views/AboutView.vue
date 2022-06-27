<template>
  <div class="about">

    <div v-if="alert" style=" margin: 15px; padding-top: 15px;">
      <v-alert type="success"
      v-model="alert"
      dismissible>
      Successfully subscribed
    </v-alert>
    </div>

    <h2 style="text-align: center; margin: 15px; padding-top: 15px;">Subscribe to NBA League Pass to get newest info about your favourite team and players</h2>
    <v-row justify="center">


      <v-dialog
        v-model="dialog"
        persistent
        max-width="600px"
        
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="primary"
            dark
            v-bind="attrs"
            v-on="on"
            style="margin: 20px"
          >
            Subscribe
          </v-btn>
        </template>
        <v-card>
          <v-card-title>
            <span class="text-h5">Subscription form</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col
                  cols="12"
                  sm="6"
                >
                  <v-text-field
                    label="First name*"
                    required
                    v-model="first_name"
                  ></v-text-field>
                </v-col>
                <v-col
                  cols="12"
                  sm="6"
                >
                  <v-text-field
                    label="Last name*"
                    required
                    v-model="last_name"
                  ></v-text-field>
                </v-col>
                <v-col cols="12">
                  <v-text-field
                    label="Email*"
                    required
                    v-model="email"
                  ></v-text-field>
                </v-col>
                <v-col
                  cols="12"
                  sm="6"
                >
                  <v-select
                    :items="['0-17', '18-29', '30-54', '54+']"
                    label="Age*"
                    required
                    v-model="age"
                  ></v-select>
                </v-col>
                <v-col
                  cols="12"
                  sm="6"
                >
                  <v-autocomplete
                    :items="teams"
                    label="Favourite team"
                    v-model="favourite_team"
                  ></v-autocomplete>
                </v-col>
              </v-row>
            </v-container>
            <small>*indicates required field</small>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
            >
              Close
            </v-btn>
            <v-btn
              color="blue darken-1"
              text
              @click="saveSubscription()"
            >
              Save
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
  export default {
    data: () => ({
      dialog: false,
      alert: false,
      first_name: '',
      last_name: '',
      email: '',
      age: '',
      favourite_team: '',
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
      saveSubscription: function(){
        this.dialog = false
        this.alert = true
        
        if((this.first_name == '') || (this.last_name == '') || (this.age == '') || (this.email == '')){
          alert('Please fill all of the required fields')
          this.dialog = true
          this.alert = false
        } else {
          this.first_name = ''
          this.last_name = ''
          this.age = ''
          this.email = ''
          this.favourite_team = ''
        }
        
      }
    }
  }
</script>




