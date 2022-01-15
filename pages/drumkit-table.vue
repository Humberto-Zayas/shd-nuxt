<template>
  
  <div>
      
      <v-data-table
        @click:row="newSample($event), playTrack($event)"
        @item-selected="loadPlaySample($event)"
        show-select
        v-model="selected"
        :headers="headers"
        :items="desserts"
        :single-select="singleSelect"
        item-key="name"
        class="elevation-1"
      >
      </v-data-table>

      <drum-preview ref="drumplayer" :sources="currentSample"></drum-preview>
  </div>

  
</template>

<script>
import DrumPreview from '~/components/DrumPreview.vue'
  export default {
  components: { DrumPreview },
    data: () => ({
        currentSound: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav',
        singleSelect: true,
        selected: [{
            name: 'Ancient Discovery Kick',
            src: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: '1%',
          }],
        headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Calories', value: 'calories' },
          { text: 'Fat (g)', value: 'fat' },
          { text: 'Carbs (g)', value: 'carbs' },
          { text: 'Protein (g)', value: 'protein' },
          { text: 'Iron (%)', value: 'iron' },
        ],
        desserts: [
          {
            name: 'Ancient Discovery Kick',
            src: 'audio/drumkit/kicks/Ancient-Discovery-Kick.wav',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            iron: '1%',
          },
          {
            name: 'Baths n Castles Kick',
            src: 'audio/drumkit/kicks/Baths-n-Castles-Kick.wav',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            iron: '1%',
          },
          {
            name: 'Chaotic Neutral Kick',
            src: 'audio/drumkit/kicks/Chaotic-Neutral-Kick.wav',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            iron: '7%',
          },
          
        ],
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
      newSample(event) {
       
        return Promise.resolve(this.currentSample = event.item.src)
        
        
        
        
      },
      playTrack() {
        // this.$refs.drumplayer.stop()
        this.$refs.drumplayer.play()
      },
      loadPlaySample(event) {
       return this.newSample(event)
       .then(this.playTrack())
      }
    }
  }
</script>

<style>

</style>