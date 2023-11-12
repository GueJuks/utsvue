<template>
    <!-- <v-container class="fill-height">
      <v-responsive class="align-center text-center fill-height">
        <v-img height="300" src="@/assets/logo.svg" />
  
        <div class="text-body-2 font-weight-light mb-n1">Welcome to</div>
  
        <h1 class="text-h2 font-weight-bold">Vuetify</h1>
  
        <div class="py-14" />
  
        <v-row class="d-flex align-center justify-center">
          <v-col cols="auto">
            <v-btn href="https://vuetifyjs.com/components/all/" min-width="164" rel="noopener noreferrer" target="_blank"
              variant="text">
              <v-icon icon="mdi-view-dashboard" size="large" start />
  
              Components
            </v-btn>
          </v-col>
  
          <v-col cols="auto">
            <v-btn color="primary" href="https://vuetifyjs.com/introduction/why-vuetify/#feature-guides" min-width="228"
              rel="noopener noreferrer" size="x-large" target="_blank" variant="flat">
              <v-icon icon="mdi-speedometer" size="large" start />
  
              Get Started
            </v-btn>
          </v-col>
  
          <v-col cols="auto">
            <v-btn href="https://community.vuetifyjs.com/" min-width="164" rel="noopener noreferrer" target="_blank"
              variant="text">
              <v-icon icon="mdi-account-group" size="large" start />
  
              Community
            </v-btn>
          </v-col>
        </v-row>
      </v-responsive>
    </v-container> -->
  
    <v-img height="300" src="@/assets/logo.svg" />
  
    <v-container>
      <p>Message is: {{ message }}</p>
      <v-text-field v-model="message" label="Edit me"></v-text-field>
  
      <!-- <v-data-table :items="itemr"></v-data-table> -->
    </v-container>
  
    <v-container>
      <v-card-title>
        Input Data Pengguna
      </v-card-title>
      <v-card-text>
        <v-form @submit.prevent="handleSubmit">
          <v-text-field v-model="userData.name" label="Nama" required></v-text-field>
  
          <v-text-field v-model="userData.email" label="Email" required type="email"></v-text-field>
  
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-card-text>
  
      <v-card v-for="(user, index) in users" :key="index">
        <v-card-title>Data Pengguna {{ index + 1 }}</v-card-title>
        <v-card-text>
          <p><strong>Nama:</strong> {{ user.name }}</p>
          <p><strong>Email:</strong> {{ user.email }}</p>
        </v-card-text>
      </v-card>
    </v-container>
  
    <v-container class="pa-4 text-center">
      <v-row class="fill-height" align="center" justify="center">
        <template v-for="(item, i) in items" :key="i">
          <v-col cols="12" md="4">
            <v-hover v-slot="{ isHovering, props }">
              <v-card :elevation="isHovering ? 12 : 2" :class="{ 'on-hover': isHovering }" v-bind="props">
                <v-img :src="item.img" height="225px" cover>
                  <v-card-title class="text-h6 text-white d-flex flex-column">
                    <p class="mt-4">
                      {{ item.title }}
                    </p>
  
                    <div>
                      <p class="ma-0 text-body-1 font-weight-bold">
                        {{ item.text }}
                      </p>
                      <p class="text-caption font-weight-medium">
                        {{ item.subtext }}
                      </p>
                    </div>
                  </v-card-title>
                  <div class="align-self-center">
                    <v-btn v-for="(icon, index) in icons" :key="index" variant="text" :class="{ 'show-btns': isHovering }"
                      :color="transparent" :icon="icon"></v-btn>
                  </div>
                </v-img>
              </v-card>
            </v-hover>
          </v-col>
        </template>
      </v-row>
    </v-container>
  
    <v-container>
      <v-row>
        <v-col v-for="n in 9" :key="n" class="d-flex child-flex" cols="4">
          <v-img :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`" aspect-ratio="1" cover class="bg-grey-lighten-2">
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular indeterminate color="grey-lighten-5"></v-progress-circular>
              </v-row>
            </template>
          </v-img>
        </v-col>
      </v-row>
    </v-container>
  
    <v-footer class="bg-indigo-lighten-1 text-center d-flex flex-column">
      <div>
        <v-btn v-for="icon in iconfooter" :key="icon" class="mx-4" :icon="icon" variant="text"></v-btn>
      </div>
  
      <div class="pt-0">
        Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut
        risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis
        commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus
        iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus
        et magnis dis parturient montes, nascetur ridiculus mus.
      </div>
  
      <v-divider></v-divider>
  
      <div>
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </div>
    </v-footer>
  </template>
  
  <!-- <script setup>
    //
  </script> -->
  
  <style scoped>
  .v-card {
    transition: opacity .4s ease-in-out;
  }
  
  .v-card:not(.on-hover) {
    opacity: 0.6;
  }
  
  .show-btns {
    color: rgba(255, 255, 255, 1) !important;
  }
  </style>
  
  <script>
  export default {
    data: () => ({
      icons: [
        'mdi-rewind',
        'mdi-play',
        'mdi-fast-forward',
      ],
      iconfooter: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
      items: [
        {
          title: 'New Releases',
          text: `It's New Release Friday`,
          subtext: 'Newly released songs.',
          img: 'https://cdn.vuetifyjs.com/docs/images/cards/hands.jpg',
        },
        {
          title: 'Rock',
          text: 'Greatest Rock Hits',
          subtext: 'Lose yourself in rock tunes.',
          img: 'https://cdn.vuetifyjs.com/docs/images/cards/singer.jpg',
        },
        {
          title: 'Mellow Moods',
          text: 'Ambient Bass',
          subtext: 'Chill beats to mellow you out.',
          img: 'https://cdn.vuetifyjs.com/docs/images/cards/concert.jpg',
        },
      ],
      transparent: 'rgba(255, 255, 255, 0)',
      message: '',
      // itemr: [
      //   {
      //     name: 'African Elephant',
      //     species: 'Loxodonta africana',
      //     diet: 'Herbivore',
      //     habitat: 'Savanna, Forests',
      //   },
      // ],
      userData: {
        name: '',
        email: '',
      },
      users: [],
    }),
    methods: {
      handleSubmit() {
        // Tambahkan data pengguna ke array
        this.users.push({ ...this.userData });
  
        // Bersihkan formulir setelah data ditambahkan
        this.userData.name = '';
        this.userData.email = '';
      },
    },
  }
  </script>
  