<template>
  <v-container
    id="team"
    dark
    class="primary darken-1 white--text fluid text-xs-center"
  >
    <v-layout
row wrap
>
      <v-flex
        v-for="member in team"
        :key="member.name"
        xs12
        sm6
        class="text-xs-center mt-3 mb-2"
      >
        <v-avatar
          class="accent mb-4"
          size="150"
          style="display: block; margin: 0 auto;"
        >
          <img
:alt="member.name" :src="'/img/profiles/' + member.image" />
        </v-avatar>
        <h3
class="headline mb-2" v-text="member.name" />
        <span
class="subheading" v-text="member.subtitle" />
        <v-flex class="mt-2">
          <v-btn
            v-for="link in member.links"
            :key="member.name + link.icon"
            fab
            flat
            dark
            :href="link.url"
            target="_blank"
            small
            :color="link.color"
            aria-hidden="true"
            rel="noopener"
          >
            <v-icon dark>
              {{ link.icon }}
            </v-icon>
          </v-btn>
        </v-flex>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script lang="ts">
  import Vue from "vue";
  import { Component } from "vue-property-decorator";

  @Component({
    data() {
      return {
        team: [
          {
            name: "Peter Kazazes",
            subtitle: "Wave Rider",
            image: "peter.jpg",
            links: [
              {
                icon: "mdi-email",
                url: "mailto:peter@sibylvision.com",
                color: "blue-grey lighten-3",
              },
              {
                icon: "mdi-github-circle",
                url: "https://github.com/kazazes",
                color: "blue-grey lighten-4",
              },
              {
                icon: "mdi-linkedin",
                url: "https://linkedin.com/in/kazazes",
                color: "blue-grey lighten-4",
              },
              {
                icon: "mdi-twitter",
                url: "//twitter.com/pkcodes",
                color: "blue-grey lighten-4",
              },
            ],
          },
          {
            name: "Luke Berndt",
            subtitle: "Static Squelcher",
            image: "luke.jpg",
            links: [
              {
                icon: "mdi-email",
                url: "mailto:luke@sibylvision.com",
                color: "blue-grey lighten-3",
              },
              {
                icon: "mdi-github-circle",
                url: "https://github.com/robotastic",
                color: "blue-grey lighten-4",
              },
              {
                icon: "mdi-linkedin",
                url: "https://www.linkedin.com/in/robotastic/",
                color: "blue-grey lighten-4",
              },
              {
                icon: "mdi-twitter",
                url: "https://twitter.com/lukeberndt",
                color: "blue-grey lighten-4",
              },
            ],
          },
        ],
      };
    },
  })
  export default class AboutView extends Vue {}
</script>

<style lang="scss">
  .v-avatar img {
    border: 2px solid #5a5e69;
  }
</style>
