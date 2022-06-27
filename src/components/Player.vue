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
    
    <v-card-title class="justify-center">{{ player.first_name + ' ' + player.last_name}}</v-card-title>

    <v-card-text style="color: blue; text-align: center;">
      <div>Position: {{ player.position}}</div>
      <div>Height feet: {{ player.height_feet}}</div>
      <div>Height inches: {{ player.height_inches}}</div>
      <div>Weight pounds: {{ player.weight_pounds}}</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title class="justify-center">{{ player.team.full_name}}</v-card-title>

  </v-card>
</template>

<script>
  export default {
    name: 'PlayerComponent',
    props: ['player']
  }
</script>
