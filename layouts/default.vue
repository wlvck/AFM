<template>
  <v-app dark>
    <v-main>
      <v-container>
        <h2 class="header__name">Поиск клиента в АФМ</h2>
        <Nuxt/>
      </v-container>
    </v-main>
    <v-footer
      dark
      padless
    >
      <v-card
        flat
        tile
        style="width: 100%; background: #00805f"
        class="white--text text-center"
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4 white--text"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text pt-0">
          Сервис позволяет найти клиента в списке агенства финансового мониторинга
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          <strong>Агентство по финансовому мониторингу</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
