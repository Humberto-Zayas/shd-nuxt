<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <NuxtLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline">
          Digital eCommerce Application Demo
        </v-card-title>
        <v-card-text>
          <div data-netlify-identity-button></div>

          <p>Each page route represents a feature for either ecommerce or audio playback in the browser. </p>
          
          
          <p>Thanks for checking this demo out. All pages and UI is work in progress and meant to practice different implementations.</p>
          <div class="text-xs-right">
            <em><small>&mdash; Humberto Zayas</small></em>
          </div>
          <hr class="my-3">
          <a
            href="https://soundsinhd.com"
            target="_blank"
            rel="noopener noreferrer"
          >
            Sounds in HD
          </a>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
