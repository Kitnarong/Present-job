<template>
  <v-app>
    <v-container>
      <nuxt />
      <v-row align="center" justify="center">
        <v-col cols="12" sm="8" md="4" align="center">
          <v-img
            width="50%"
            src="https://d2k1ftgv7pobq7.cloudfront.net/meta/c/p/res/images/trello-header-logos/167dc7b9900a5b241b15ba21f8037cf8/trello-logo-blue.svg"
          ></v-img>
          <br />
          <v-card class="elevation-4 text-left">
            <v-card-title class="justify-center align-center">
              <h5 class="login-terllo">Log in to Trello</h5>
            </v-card-title>
            <v-card-text>
              <v-form @submit="login">
                <v-text-field
                  placeholder="Enter email"
                  solo
                  type="text"
                  v-model="auth.email"
                ></v-text-field>

                <v-text-field
                  
                  placeholder="Enter password"
                  solo
                  type="password"
                  v-model="auth.password"
                ></v-text-field>
              </v-form>
              <v-btn
                type="submit"
                block
                color="success"
                @submit="login"
                @click="login"
                >Log in</v-btn
              >
              <br />
              <h3 class="or">OR</h3>
              <br />
              <v-btn class="mb-3 elevation-3" block>
                <v-icon color="red">mdi-google</v-icon>
                &nbsp; <span>Continue with Google</span>
              </v-btn>

              <v-btn class="mb-3 elevation-3" block>
                <v-icon color="blue">mdi-microsoft</v-icon>
                 &nbsp; <span>Continue with microsoft</span>
                
                </v-btn>
              <v-btn class="mb-3 elevation-3" block>
                <v-icon>mdi-apple</v-icon>&nbsp; Continue with apple
              </v-btn>

              <br />
            </v-card-text>
          </v-card>
          <v-snackbar :timeout="4000" v-model="snackbar" absolute bottom center>
            {{ snackbarText }}
          </v-snackbar>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  layout: 'signin',
  data() {
    return {
      snackbar: false,
      snackbarText: 'No error message',
      auth: {
        email: '',
        password: '',
      },
    }
  },
  methods: {
    login() {
      let that = this
      this.$fire.auth
        .signInWithEmailAndPassword(this.auth.email, this.auth.password)
        .catch(function (error) {
          that.snackbarText = error.message
          that.snackbar = true
        })
        .then((user) => {
          //we are signed in
          $nuxt.$router.push('/')
        })
    },
  },
}
</script>

<style></style>
