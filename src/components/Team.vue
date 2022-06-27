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

    <v-card-title class="justify-center">{{ team.full_name}}</v-card-title>
    
    <v-card-text style="color: blue; text-align: center;">
      <div>Conference: {{ team.conference }} </div>
      <div>Division: {{ team.division }} </div>
      <div>City: {{ team.city }}</div>
      <div>Brand name: {{ team.name }}</div>
      <div>Short: {{ team.abbreviation }}</div>
      <div>ID: {{ team.id }}</div>
    </v-card-text>

  </v-card>
</template>

<script>
  export default {
    name: 'TeamComponent',
    props: ['team']
  }
</script>
