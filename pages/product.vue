<template>
    <v-row justify="center" align="center">
        <v-col cols="12" sm="8" md="6">
            <v-card>
                <v-card-title>
                    Drum Kit Tree
                </v-card-title>
                <template>
                    <v-treeview
                        @update:active="playTrack()"
                        return-object
                        activatable
                        :items="items"
                    >
                      <template v-slot:label="{ item }">
                        
                        <span v-if="item.src"  @click="newSample(item)">{{item.name}}</span>
                        <span v-else>{{item.name}}</span>
                      </template>
                    </v-treeview>
                </template>
            </v-card>
        </v-col>
        <drum-preview ref="drumplayer" :sources="temp"></drum-preview>
    </v-row>
</template>

<script>
import DrumPreview from '~/components/DrumPreview.vue'
  export default {
  components: { DrumPreview },
    data: () => ({
      temp: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav',
      currentSample: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav',
      audioSources: [
          "audio/drumkit/kicks/Ancient-Discovery-Kick.wav",
          "audio/drumkit/kicks/Baths-n-Castles-Kick.wav",
          "audio/drumkit/kicks/Chaotic-Neutral-Kick.wav",
          "audio/drumkit/kicks/Cowpoke Kick.wav",
          "audio/drumkit/Ancient Discovery Snare.wav",
          "audio/drumkit/Baths n Castles Treasure Chest.wav",
          "audio/drumkit/Baths n Castles Treasure Snare Clap.wav",
          "audio/drumkit/Chaotic Neutral Snare.wav",
          "audio/drumkit/Ancient Discovery Hat 01.wav",
          "audio/drumkit/Ancient Discovery Hat 02.wav",
          "audio/drumkit/Ancient Discovery Hat 03.wav",
          "audio/drumkit/12 Paces Cowpoke Drum Loop 83 BPM.wav",
          "audio/drumkit/Ancient Discovery Drum Loop 110 Bpm.wav",
      ],
      items: [
        {
          id: 1,
          name: 'Kicks :',
          children: [
            { id: 2, name: 'Ancient Discovery Kick', src: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav' },
            { id: 3, name: 'Baths n Castles Kick', src: 'audio/drumkit/kicks/Baths-n-Castles-Kick.wav' },
            { id: 4, name: 'Chaotic Neutral Kick', src: 'audio/drumkit/kicks/Chaotic-Neutral-Kick.wav' },
          ],
        },
        {
          id: 5,
          name: 'Snares :',
          children: [
            { id: 5, name: 'Ancient Discovery Snare', src: '' },
            { id: 6, name: 'Baths n Castles Treasure Chest', src: '' },
            { id: 7, name: 'Baths n Castles Treasure Snare Claps', src: '' },
          ],
        },
        {
          id: 15,
          name: 'Hats :',
          children: [
            { id: 16, name: 'Ancient Discovery Hat 01', src: '' },
            { id: 17, name: 'Ancient Discovery Hat 02', src: '' },
            { id: 18, name: 'Ancient Discovery Hat 03', src: '' },
          ],
        },
        {
          id: 19,
          name: 'Loops :',
          children: [
            
            { id: 24, name: '12 Paces Cowpoke Drum Loop 83 BPM', src: '' },
            { id: 25, name: 'Ancient Discovery Drum Loop 110 BPM', src: '' },
          ],
        },
      ],
    }),
    methods: {
      newSample(value) {
        // if (value[0].length > 1) {
        //   this.temp = value[0].src
        // }
        this.temp = value.src
        
      },
      playTrack(value) {
        
        this.$refs.drumplayer.togglePlayback()
      },
    }
  }
</script>