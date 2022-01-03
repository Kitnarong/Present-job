<template>
  <v-app>
    <v-container>
      <v-row class="justify-center algin-left mt-1">
        <v-col cols="12" md="8">
          <v-app-bar height="44px" color="primary" v-model="appBar" fixed>
            <v-btn icon>
              <v-icon>mdi-dots-grid mdi-light</v-icon>
            </v-btn>
            <nuxt-link to="/">
              <v-btn icon>
                <v-icon>mdi-trello mdi-light</v-icon>
              </v-btn>
            </nuxt-link>
            <nuxt-link to="/">
              <h2 class="trello-logo">Trello</h2>
            </nuxt-link>
            <v-spacer></v-spacer>
            <v-menu
              transition
              v-model="menu"
              :close-on-content-click="false"
              :nudge-width="100"
              :nudge-bottom="1"
              :nudge-right="10"
              offset-y
            >
              <template v-slot:activator="{ on, attrs }">
                <v-btn icon v-bind="attrs" v-on="on">
                  <v-icon>mdi-account mdi-light</v-icon>
                </v-btn>
              </template>
              <v-card>
                <v-list-item-content>
                  <v-list-item-subtitle class="center"
                    >Account</v-list-item-subtitle
                  >
                </v-list-item-content>
                <v-divider></v-divider>
                <v-list>
                  <v-list-item>
                    <v-list-item-avatar>
                      <img
                        src="https://cdn.vuetifyjs.com/images/john.jpg"
                        alt="John"
                      />
                    </v-list-item-avatar>
                    <v-list-item-content>
                      <v-list-item-title>Sign as in</v-list-item-title>
                      <v-list-item-subtitle>{{
                        $nuxt.$fire.auth.currentUser.email
                      }}</v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>
                </v-list>
                <v-divider></v-divider>
                <v-list>
                  <v-list-item>
                    <v-list-item-title class="d-flex flex-column align-center">
                      <v-btn
                        class="logout"
                        color="primary"
                        flat
                        to="/auth/signout"
                        nuxt
                      >
                        <v-icon>mdi-exit-to-app</v-icon>&nbsp;&nbsp;
                        <b>Log out</b>
                      </v-btn>
                    </v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-card>
            </v-menu>
          </v-app-bar>
        </v-col>
      </v-row>
    </v-container>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {}
</script>
