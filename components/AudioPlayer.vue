<template>
  <div>
    
    <span>Total duration: {{ duration | minutes }} seconds</span>
    <span> Seek: {{seek | minutes }}</span>

    
    
    <template>
      
      <br>
      Normal Bar tied to progress no interaction
      
      <!-- <v-progress-linear 
        height="25"
        v-model="seek"
        @change="setSeek(seek)"
       >
      </v-progress-linear> -->

      <v-progress-linear 
        height="25"
        v-model="seek"
        @change="setSeek(seek)"
       >
      </v-progress-linear>

      <!-- Slider Bar 
      <v-slider
        hint="Im a hint"
        
        :max="duration"
        min="0"
      ></v-slider> -->
     
    </template>
    <!-- <span>Progress: {{ (progress * 100) }}%</span> -->
    <button @click="togglePlayback">{{ playing ? 'Pause' : 'Play' }}</button>
    <button @click="stop">Stop</button>
    <button @click="toggleMute">{{ toggleMute ? 'mute': 'unmute' }}</button>
  </div>
</template>

<script>
  import VueHowler from 'vue-howler'
 
  export default {
    props: ['sources', 'playlist'],
    mixins: [VueHowler],
    data () {
      return {
        seekvalue: 0,
        update: null
      }
    },
    methods: {
      bullshit(event) {
        this.update = event
      }
    }
  }
</script>

