<template>
  <v-container class="content-wrapper">
    <v-layout class="column">
      <v-row class="hero-container">
        <v-col class="testimonial-container" :cols="6">
          <h1>Deine Webseite für Jobs</h1>

          <v-carousel class="testimonial-carousel" :show-arrows="showArrows">
            <v-carousel-item v-for="testimonial in testimonials" :key="testimonial">
              <v-sheet :color="testimonial_bg_color" height="100%">
                <v-layout class="testimonial column">
                  <v-layout class="headshots column mx-auto mb-5">
                    <v-img
                      class="headshot"
                      v-for="(headshot, i) in testimonial.headshots"
                      :key="headshot"
                      :src="headshot"
                      :height="i == 0 ? 90 : 60"
                      :width="i == 0 ? 90 : 60"
                      :style="i == 1 ? 'margin-top: -45px;' : ''"
                    />
                  </v-layout>

                  <p class="text-center mb-0">
                    <label class="name">
                      <strong>{{testimonial.name}}</strong>
                    </label>
                  </p>

                  <p class="text-center job-title">{{testimonial.job_title}}</p>

                  <p class="text-center quote">{{testimonial.quote}}</p>
                </v-layout>
              </v-sheet>
            </v-carousel-item>
          </v-carousel>
        </v-col>

        <div class="flex-grow-1" />

        <v-col :cols="4">
          <v-layout class="column signup-form">
            <h3 class="text-center mb-5">
              Ich möchte mich jetzt
              <br />kostenlos registrieren
            </h3>

            <p class="text-center">
              Registrieren Sie sich mit Ihrem Social
              <br />Media Konto an.
            </p>

            <v-btn class="my-3">mit google registrieren</v-btn>
            <v-btn class="my-3">mit fACEBOOK registrieren</v-btn>

            <p class="text-center">
              oder registrieren Sie sich mit Ihrer E-Mail-
              <br />Adresse an.
            </p>

            <v-form ref="form" v-model="valid">
              <v-text-field label="Vorname" required></v-text-field>
              <v-text-field label="Familienname" required></v-text-field>
              <v-text-field label="Private E-Mail-Adresse" required></v-text-field>
            </v-form>

            <p class="text-center">
              <small>Sie erklären sich mit der Nutzervereinbarung, der Datenschutzrichtlinie und der Cookie-Richtlinie von TEMPI einverstanden.</small>
            </p>

            <v-layout class="column form-action-container">
              <v-btn class="submit my-5">Kostenlos Registrieren</v-btn>

              <p class="text-center">
                <a>überspringen</a>
              </p>
            </v-layout>
          </v-layout>
        </v-col>
      </v-row>

      <v-row class="clients-container">
        <v-col class="client" :cols="12" v-for="client in clients" :key="client">
          <v-layout class="column">
            <div class="client-banner">
              <v-img :src="client.banner_src" />
              <h3 class="client-title">{{client.title}}</h3>
            </div>

            <v-content>
              <v-row class="mx-auto" align="center">
                <v-img class="circle-img" :src="client.logo_src" max-width="90" max-height="90" />

                <p class="mb-0 px-3">
                  {{client.name}}
                  <br />
                  {{client.summary}}
                </p>
              </v-row>

              <p class="text-center">
                <a class="text-uppercase">anschauen & bewerben</a>
              </p>
            </v-content>
          </v-layout>
        </v-col>
      </v-row>

      <v-row>
        <v-col>
          <v-btn class="text-uppercase col-12">mehr Jobs</v-btn>
        </v-col>
      </v-row>

      <v-row class="portfolios-container mb-5">
        <v-col
          class="portfolio fill-height"
          :cols="4"
          v-for="portfolio in portfolios"
          :key="portfolio"
        >
          <v-card class="pa-3 fill-height">
            <v-layout class="column fill-height">
              <v-img class="mx-auto mt-auto" :src="portfolio.image_src" width="240" :contain="true" />

              <label>
                <strong>{{portfolio.title}}</strong>
              </label>
              <p>{{portfolio.summary}}</p>
            </v-layout>
          </v-card>
        </v-col>
      </v-row>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      testimonial_bg_color: "rgba(255, 255, 255, 0.84)",
      testimonials: [
        {
          headshots: [
            require("@/assets/images/headshot (3).png"),
            require("@/assets/images/headshot (2).png")
          ],
          name: "Markus H.",
          job_title: "Brandschutz Consulting",
          quote:
            "Tempi ermöglicht uns eine schnelle und einfache Abwicklung auf der Suche nach neuen Mitarbeiter."
        },
        {
          headshots: [require("@/assets/images/headshot (1).png")],
          name: "Gianluca F.",
          job_title: "Arbeitnehmer",
          quote:
            "Einen neuen Job auf Tempi zu finden war für mich sehr einfach."
        },
        {
          headshots: [
            require("@/assets/images/headshot (4).png"),
            require("@/assets/images/headshot (5).png")
          ],
          name: "Robert Mosser-Waller",
          job_title: "Gesamtschulleitung Pestalozzi Schulen",
          quote:
            "Dank Tempi können wir schnell und gezielt Mitarbeiter akquirieren."
        }
      ],
      showArrows: false,
      clients: [
        {
          banner_src: require("@/assets/images/NoPath - Kopie (3)-1.png"),
          logo_src: require("@/assets/images/NoPath.png"),
          title: "Crewmitarbeiter/IN",
          name: "McDonald's",
          summary: "﻿8105 Regensdorf"
        },
        {
          banner_src: require("@/assets/images/NoPath - Kopie (4).png"),
          logo_src: require("@/assets/images/NoPath - Kopie.png"),
          title: "Senior Accountant",
          name: "LIPO Einrichtungsmärkte AG",
          summary: "4133 Pratteln"
        },
        {
          banner_src: require("@/assets/images/NoPath - Kopie (5).png"),
          logo_src: require("@/assets/images/NoPath - Kopie (2)-1.png"),
          title: "Hauswart (m/w)",
          name: "ISS Facility Services AG",
          summary: "4126 Bettingen"
        }
      ],
      portfolios: [
        {
          image_src: require("@/assets/images/SVGZeichenfläche 10.png"),
          title: "Schritt 1",
          summary: "Erstellen Sie Ihr Profil"
        },
        {
          image_src: require("@/assets/images/SVGZeichenfläche 19.png"),
          title: "Schritt 2",
          summary: "Lassen Sie sich finden oder suche den passenden Job"
        },
        {
          image_src: require("@/assets/images/SVG02Zeichenfläche 18.png"),
          title: "Schritt 3",
          summary: "Bewerben Sie sich mit einem Klick"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
.testimonial-container {
  .v-carousel__controls {
    background-color: transparent;

    .v-carousel__controls__item {
      color: #546e7a;

      &.v-item--active {
        color: #fff;
        &:before {
          background-color: rgba(0, 0, 0);
          opacity: 0.1;
        }
      }
    }
  }
}
</style>

<style lang="scss" scoped>
.content-wrapper {
  padding: 0 300px;
  h1 {
    font-size: 56px;
  }
  h3 {
    font-size: 24px;
  }

  .hero-container {
    height: 100vh;
    margin-top: 100px;

    &,
    * {
      color: #546e7a;
    }

    .testimonial-container {
      h1 {
        color: #fff;
        text-shadow: 0px 3px 6px rgba(0, 0, 0, 0.16);
        margin-bottom: 60px;
      }

      .testimonial {
        padding: 70px 30px;

        .headshots {
          width: 120px;

          .headshot:first-child {
            margin-left: auto;
          }

          .headshot:last-child {
            margin-right: auto;
          }
        }
      }
    }

    .signup-form {
      padding: 28px;
      background-color: rgba(255, 255, 255, 0.84);
      box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);

      .form-action-container {
        background-color: #f5f5f5;
        margin-left: -28px;
        margin-right: -28px;
        margin-bottom: -28px;
        padding: 0 28px;

        .submit {
          color: #ffffff;
          background-color: #2196f3;
        }
      }
    }
  }

  .clients-container {
    .client {
      .client-banner {
        position: relative;

        .client-title {
          color: #fff;
          position: absolute;
          bottom: 0px;
          padding: 0 16px;
        }
      }

      .v-content {
        background-color: #fff;
        padding: 16px !important;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.2);

        .circle-img {
          border-radius: 50%;
          overflow: hidden;
          background-color: #fff;
          box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.16);
        }
      }
    }
  }

  .portfolios-container {
    .portfolio {
    }
  }
}
</style>
