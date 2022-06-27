<template>
  <v-card
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

  </v-card>
</template>

<script>
  export default {
    name: 'GameComponent',
    props: ['game']
  }
</script>
