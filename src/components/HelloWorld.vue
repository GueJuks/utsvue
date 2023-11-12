<template>
  <v-app id="inspire">

    <v-main class="bg-black">
      <v-container class="my-container">

        <v-row>
          <!-- Sidebar(Kalau di HTML aside) -->
          <v-col cols="3">
            <v-sheet rounded="lg" class="bg-grey-darken-4">
              <!-- <v-list rounded="lg"> -->
                <!-- <v-list-item v-for="n in 1" :key="n" link :title="`List Item ${n}`"></v-list-item> -->
                <v-card-title>
                  Input Data Pengguna
                </v-card-title>

                <!-- Form Input Pengguna -->
                <v-card-text>
                  <v-form @submit.prevent="handleSubmit">
                    <v-text-field v-model="userData.name" label="Nama" required></v-text-field>

                    <v-text-field v-model="userData.email" label="Email" required type="email"></v-text-field>

                    <v-btn type="submit" color="primary">Submit</v-btn>
                  </v-form>
                </v-card-text>
                <!-- Akhir FOrm Input Pengguna -->

                <!-- Data yang diinput -->
                <v-card v-for="(user, index) in users" :key="index">
                  <v-card-title>Data Pengguna {{ index + 1 }}</v-card-title>
                  <v-card-text>
                    <p><strong>Nama:</strong> {{ user.name }}</p>
                    <p><strong>Email:</strong> {{ user.email }}</p>
                  </v-card-text>
                </v-card>
                <!-- Akhir Data yang diinput -->

                <!-- <v-divider class="my-2"></v-divider> -->

                <!-- <v-list-item color="grey-lighten-4" link title="Refresh"></v-list-item> -->
              <!-- </v-list> -->
            </v-sheet>
          </v-col>
          <!-- Akhir Sidebar -->

          <!-- Halaman Utama -->
          <v-col>
            <v-sheet min-height="70vh" rounded="lg" class="bg-grey-darken-4">
              <!-- Gambar Spotify -->
              <v-img height="300" :src="'https://www.pngplay.com/wp-content/uploads/12/Spotify-Logo-Transparent-Images.png'" />
              <!-- Akhir Gambar Spotify -->

              <!-- List / Data Music -->
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
                              <v-btn v-for="(icon, index) in icons" :key="index" variant="text"
                                :class="{ 'show-btns': isHovering }" :color="transparent" :icon="icon"></v-btn>
                            </div>
                          </v-img>
                        </v-card>
                      </v-hover>
                    </v-col>
                  </template>
                </v-row>
              </v-container>
              <!-- Akhir List/Data Music -->

              <!-- Data gambar -->
              <v-container>
                <v-row>
                  <v-col v-for="n in 9" :key="n" class="d-flex child-flex" cols="4">
                    <v-img :src="`https://picsum.photos/500/300?image=${n * 5 + 10}`"
                      :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}`" aspect-ratio="1" cover
                      class="bg-grey-lighten-2">
                      <template v-slot:placeholder>
                        <v-row class="fill-height ma-0" align="center" justify="center">
                          <v-progress-circular indeterminate color="grey-lighten-5"></v-progress-circular>
                        </v-row>
                      </template>
                    </v-img>
                  </v-col>
                </v-row>
              </v-container>
              <!-- Akhir Data Gambar -->

            </v-sheet>
          </v-col>
          <!-- Akhir Halaman Utama -->
        </v-row>

        <br>

        <!-- Footer -->
        <v-footer class="bg-grey-darken-4 rounded text-center d-flex flex-column">
          <div>
            <v-btn v-for="icon in iconfooter" :key="icon" class="mx-4" :icon="icon" variant="text"></v-btn>
          </div>

          <div class="pt-0">
            Web Company Profile Music
          </div>

          <v-divider></v-divider>

          <div>
            {{ new Date().getFullYear() }} — <strong>UTS Vue Js</strong>
          </div>
        </v-footer>
        <!-- Akhir Footer -->

      </v-container>
    </v-main>
  </v-app>
</template>


<!-- Style -->
<style>
.my-container {
  max-width: 1200px;
  /* Sesuaikan nilai sesuai kebutuhan Anda */
  margin: auto;
  /* Untuk membuat container berada di tengah layar */
  .v-card {
    transition: opacity .4s ease-in-out;
  }

  .v-card:not(.on-hover) {
    opacity: 0.6;
  }

  .show-btns {
    color: rgba(255, 255, 255, 1) !important;
  }
}
</style>
<!-- Akhir Style -->

<script setup>
// const links = [
//   'Dashboard',
//   'Messages',
//   'Profile',
//   'Updates',
// ]
</script>

<!-- Script Data -->
<script>
export default {
  data: () => ({
    links: [
      'Dashboard',
      'Messages',
      'Profile',
      'Updates',
    ],
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
<!-- Akhir Script Data -->