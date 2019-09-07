<template>
  <v-app class="app-wrapper">
    <v-content id="parallax-hero">
      <v-img :src="parallax_src" />
    </v-content>

    <v-content>
      <v-app-bar class="header-bar" relative>
        <v-container fluid>
          <v-row>
            <div class="logo-container">
              <a class="logo">
                <v-img :src="logo_src" max-width="165" />
              </a>
            </div>

            <div class="flex-grow-1" />

            <a class="login-btn">LOGIN</a>
          </v-row>
        </v-container>
      </v-app-bar>

      <v-content>
        <nuxt />
      </v-content>

      <v-footer class="footer-container" relative>
        <v-container>
          <v-row>
            <v-col class="ml-auto" :cols="3">
              <p>
                <label>Social Media</label>
              </p>

              <v-layout>
                <v-img :src="logo_solo_src" max-width="30" />
              </v-layout>
            </v-col>

            <v-col :cols="3">
              <p>
                <label>Unternehmen</label>
              </p>

              <v-layout column>
                <a>Jobs</a>
                <a>Blog</a>
                <a>Investor</a>
                <a>Kontaktiere uns</a>
              </v-layout>
            </v-col>

            <v-col class="mr-auto" :cols="3">
              <p>
                <label>Legal</label>
              </p>

              <v-layout column>
                <a>Cookie-Richtlinie</a>
                <a>Urheberrechtsrichtlinie</a>
                <a>Datenschutzrichtlinie</a>
              </v-layout>
            </v-col>
          </v-row>
        </v-container>

        <v-container class="copy-right">
          <v-layout>
            <span>Made with</span>&nbsp;
            <v-icon color="white" small>mdi-heart</v-icon>&nbsp; & &nbsp;
            <v-icon color="white" small>mdi-coffee</v-icon>&nbsp;
            <div class="flex-grow-1" />
            <span>©TEMPI</span>
          </v-layout>
        </v-container>
      </v-footer>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      logo_src: require("../assets/images/tempi-logo-white.png"),
      logo_solo_src: require("../assets/images/logo-solo-white.png"),
      parallax_src: require("../assets/images/60.png")
    };
  }
};
</script>

<style lang="scss" scoped>
.app-wrapper {
  background-color: transparent;
}

#parallax-hero {
  position: fixed;
}

.header-bar {
  background-color: #37474f !important;

  .logo-container .logo {
    display: flex;
  }

  .login-btn {
    display: flex;
    margin: auto;
    color: #fff;
  }
}

footer {
  &.footer-container {
    background-color: #455a64;
    color: #fff;
    padding: 0;
  }

  label {
    font-weight: bold;
  }

  .layout a {
    color: #fff;
  }

  .copy-right {
    background-color: #37474f;
    padding: 16px;
    font-size: 14px;
  }
}
</style>