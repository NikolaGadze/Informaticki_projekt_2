<template>
  <div class="home" style="margin: 10px">
    
    
    <v-containter>
      <v-row>
        <v-col cols="12">
          <v-img
            src="https://imgs.search.brave.com/JZWgDAbXidlasFNtLwbmsfUnrxbdUAFJklHCO8xM24A/rs:fit:795:318:1/g:ce/aHR0cDovL3N0YXRp/Yy5pcGhvbmVsaWZl/LmNvbS9zaXRlcy9p/cGhvbmVsaWZlLmNv/bS9maWxlcy9OQkEt/TG9nby5wbmc">
          </v-img>
        </v-col>
      </v-row>
    

     <v-row>
        <v-col cols="12">
            <h2 style="text-align: center;"><b>NBA page where you can get data about active and retired players, teams and stats, as well as past, present and future games</b></h2>
        </v-col>
      </v-row>


      <v-row>
        <v-col v-for="item in items" :key="item.name" cols="12" xl="4" lg="4" md="6" sm="12" xs="12">
          <v-card
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

            <v-img
              height="250"
              :src="item.src"
            ></v-img>


            <v-row>
              <v-col cols="12" xl="12" lg="12" md="12" sm="12" xs="12">
                <v-card-title class="justify-center">{{ item.name + " : " + item.number }}</v-card-title>
              </v-col>
            </v-row>

            <v-divider class="mx-4"></v-divider>

            <v-row>
              <v-col cols="12" xl="12" lg="12" md="12" sm="12" xs="12">
                <v-card-actions class="justify-center">
                  <v-btn
                    color="primary"
                    text
                    :to="item.route"
                  >
                    {{ item.name}}
                  </v-btn>
                </v-card-actions>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <hr>
        </v-col>
      </v-row>

       <v-row>
        <v-col cols="12">

          <h1 style="text-align: center; margin: 10px;">Current champions</h1>

          <v-img
            src="https://imgs.search.brave.com/8eX9mpQ_CCTeISebkySsCHTj-6YIWchCKFLelehg8uQ/rs:fit:1200:800:1/g:ce/aHR0cHM6Ly9zMS5p/YnRpbWVzLmNvbS9z/aXRlcy93d3cuaWJ0/aW1lcy5jb20vZmls/ZXMvc3R5bGVzL2Z1/bGwvcHVibGljLzIw/MjIvMDYvMTcvbmJh/LWZpbmFscy1nb2xk/ZW4tc3RhdGUtd2Fy/cmlvcnMtYXQtYm9z/dG9uLWNlbHRpY3Mu/anBn">
          </v-img>

          <h2 style="text-align: center; margin: 10px;">Golden State Warriors</h2>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <hr>
        </v-col>
      </v-row>

       <v-row>
        <v-col cols="12">

          <h1 style="text-align: center; margin: 10px;">Most Valuable Player</h1>

          <v-img
            src="https://imgs.search.brave.com/1tJnuJJXi7ThMp8VQwQKeV7BK9qSlC-P3i_G1B7ekTA/rs:fit:1200:967:1/g:ce/aHR0cHM6Ly9ibG94/aW1hZ2VzLm5ld3lv/cmsxLnZpcC50b3du/bmV3cy5jb20vZ2F6/ZXR0ZS5jb20vY29u/dGVudC90bmNtcy9h/c3NldHMvdjMvZWRp/dG9yaWFsLzMvZGQv/M2RkY2M2N2MtNDdk/My0xMWVhLThkMDct/NGJhYjYzNTM1YTYz/LzVlM2E0YTJkZWYw/NGUuaW1hZ2UuanBn/P3Jlc2l6ZT0xNDc2/JTJDOTY3">
          </v-img>

          <h2 style="text-align: center; margin: 10px;">Nikola Jokić</h2>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <hr>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">

          <h1 style="text-align: center; margin: 10px;">Defensive player of the year</h1>

          <v-img
            src="https://imgs.search.brave.com/EHWdbbItt9xky6FjkMA0uKo56JsawycrCqkABOAvUps/rs:fit:1200:1200:1/g:ce/aHR0cHM6Ly9zLnlp/bWcuY29tL3V1L2Fw/aS9yZXMvMS4yL1cw/bzhhM3JPVWhMTnRm/WEx6SE80SVEtLX5C/L2FEMHlNRFE0TzNj/OU16QTNNanR6YlQw/eE8yRndjR2xrUFhs/MFlXTm9lVzl1L2h0/dHBzOi8vbWVkaWEu/emVuZnMuY29tL2Vu/L2F0dF9ibGVhY2hl/cl9yZXBvcnRfYXJ0/aWNsZXNfNjk0LzQy/MjNhMDk1YWFmNmRl/ZTZlMDQ0N2E5NTMw/ZDJiYTFl">
          </v-img>

          <h2 style="text-align: center; margin: 10px;">Marcus Smart</h2>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <hr>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">

          <h1 style="text-align: center; margin: 10px;">Rookie of the year</h1>

          <v-img
            src="https://imgs.search.brave.com/lAvGw_hDkCY5bvzit16SAEoJ8hrLDNCIED9O0SRvhbg/rs:fit:1200:675:1/g:ce/aHR0cHM6Ly9mYWRl/YXdheXdvcmxkLm5l/dC8uaW1hZ2UvdF9z/aGFyZS9NVGd6TWpn/NE5qTXhNRE14TlRB/MU9UVTQvc2NvdHRp/ZS1iYXJuZXMuanBn">
          </v-img>

          <h2 style="text-align: center; margin: 10px;">Scootie Barnes</h2>
        </v-col>
      </v-row>





    </v-containter>

  
  
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  data: () => ({
    items: [
      {name: 'Players', number: '3757', src: 'https://imgs.search.brave.com/c_fDH8eCaOcduxBIkqVD2U2P-i4ahGPSgH-JV5dzeaE/rs:fit:1200:1200:1/g:ce/aHR0cHM6Ly9ob29w/c2hhYml0LmNvbS93/cC1jb250ZW50L3Vw/bG9hZHMvZ2V0dHkt/aW1hZ2VzLzIwMTgv/MDgvMTIxMDk5MjA4/Ni5qcGVn', route: '/players'},
      {name: 'Teams', number: '30', src: 'https://imgs.search.brave.com/UShbzkb7Q9zIrkNwMRTcm-4KwV_5eiQYDD3Og2ZTQZU/rs:fit:1200:1080:1/g:ce/aHR0cDovL2dldHdh/bGxwYXBlcnMuY29t/L3dhbGxwYXBlci9m/dWxsLzUvNC8wLzMz/NzMyMC5qcGc', route: '/teams'},
      {name: 'Games', number: '46911', src: 'https://imgs.search.brave.com/h8gSUKUpGKiyu--mPdDzw90iSuwQkKTaCjlHiFw_Y3Y/rs:fit:1200:1200:1/g:ce/aHR0cHM6Ly9uZXdh/cmVuYS5jb20vd3At/Y29udGVudC91cGxv/YWRzLzIwMjAvMDMv/VVNBVFNJXzE0MTM2/MTE2LXNjYWxlZC5q/cGc', route: '/games'}
    ]
  })
  

}
</script>
