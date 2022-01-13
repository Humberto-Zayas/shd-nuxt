<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <h1>Playing: {{playing}}</h1>
      <v-card>
        
        <v-card-text>
         
          <template>
            <v-card height="330" :class="{playlist}">
              <v-list>
                <v-list-item 
                  v-for="(track, index) in playlist" 
                  :key="track.title"
                  @click="selectTrack(track), setSong(track), playTrack()"
                  :class="[{selected: track === selectedTrack}, {even: index % 2 == 0}]"
                >
                  <v-list-item-content
                  >
                    <v-list-item-title>
                      <v-icon v-if="currentSong.src == track.src">mdi-pause</v-icon>
                      <v-icon v-else>mdi-play</v-icon>
                      <span>{{ index | numbers }} </span>
                      {{ track.artist }}
                       - {{ track.title }}
                    </v-list-item-title>
                  </v-list-item-content>
                  <v-spacer></v-spacer>
                  <v-row justify="space-around">
                    <v-icon
                      small
                      color="white darken-2"
                    >
                      mdi-spotify 
                    </v-icon>

                    <v-icon
                      small
                      color="white darken-2"
                    >
                      mdi-soundcloud
                    </v-icon>

                    <v-icon
                      small
                      color="white darken-2"
                    >
                      mdi-youtube
                    </v-icon>

                    <v-icon
                      small
                      color="white darken-2"
                    >
                      mdi-cloud-download
                    </v-icon>

                    <v-icon
                      small
                      color="white darken-2"
                    >
                      mdi-cash
                    </v-icon>

                    
                  </v-row>
                </v-list-item>
              </v-list>
            </v-card>
          </template>
                    
          <audio-player
            @play="songPlaying"
            @pause="songPlaying"
            @stop="stopPlaying"
            ref="audioplayer"
            :playlist="playlist" 
            :sources="currentSong" 
            :loop="false">
          </audio-player>

        </v-card-text>
        
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import AudioPlayer from '~/components/AudioPlayer.vue'



export default {
  name: 'Player',
  components: {
      AudioPlayer
    },
    data () {
      return {
        playing: false,
        selectedTrack: null,
        currentSong: 'audio/dynasty.wav',
        playlist: [
          {
          title: 'Dynasty',
          artist: 'Leafygreens',
          src: 'audio/dynasty.wav'
          },
          {
          title: 'Afterblunt',
          artist: 'Leafygreens',
          src: 'audio/afterblunt.wav'
          },
          {
          title: 'Weird Trees',
          artist: 'Leafygreens',
          src: 'audio/tambo.wav'
          }
        ],
        audioSources: [
          "audio/dynasty.wav",
          "audio/afterblunt.wav",
          "audio/tambo.wav"
        ]
      }
    },
    methods: {
      setSong(audio) {
        this.currentSong = audio.src
      },
      selectTrack (track) {
        this.selectedTrack = track
      },
      playTrack() {
        this.$refs.audioplayer.togglePlayback()
      },
      songPlaying() {
        this.playing = !this.playing
      },
      stopPlaying() {
        this.playing = false
      }
    }
}
</script>

<style scoped>
  .selected {
    background-color:  rgb(216, 140, 0) !important;
  }
  .even {
    background-color: #505050
  }
  .playlist {
    overflow: auto
  }
</style>