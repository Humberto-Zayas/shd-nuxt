<template>
 
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

<style>

</style>