<template>
  <v-app-bar flat class="bg-grey-darken-4">
    <v-container class="my-container d-flex align-center justify-center">
      <v-icon>
        <img src="https://th.bing.com/th/id/R.148b28a3992349e8db92184c65d24bbd?rik=AJNg4RcAH8fwOg&riu=http%3a%2f%2forig12.deviantart.net%2f846f%2ff%2f2015%2f245%2f9%2fb%2fnew_spotify_icon_by_mattroxzworld-d98301o.png&ehk=4kqixXCdaWV6y4x6GzGcuj9iskpnJgcYXxemWAfh3cc%3d&risl=&pid=ImgRaw&r=0" alt="Custom Image" style="width: 24px; height: 24px;" />
      </v-icon>

      <v-btn v-for="link in links" :key="link" :text="link" variant="text"></v-btn>

      <v-spacer style="margin-left: 20px;"><b>UTS</b> Vue Js</v-spacer>

      <v-responsive max-width="200">
        <v-text-field density="compact" flat hide-details label="Search" rounded="lg" single-line
          variant="solo-filled"></v-text-field>
      </v-responsive>
    </v-container>
  </v-app-bar>
</template>

<style>
.my-container {
  max-width: 1200px;
  /* Sesuaikan nilai sesuai kebutuhan Anda */
  margin: auto;
}
</style>

<script setup>
//
</script>
