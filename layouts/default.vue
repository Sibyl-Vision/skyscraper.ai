<template>
  <v-app
id="sibyl" class="grey lighten-3"
>
    <v-toolbar
      v-if="navVisible"
      id="navbar"
      absolute
      app
      clipped-right
      class="grey lighten-4 elevation-1"
      style="z-index: 100;"
    >
      <v-layout
align-center justify-space-between
row fill-height
>
        <v-flex grow>
          <v-toolbar-title>
            <h1 class="headline">
              <a href="/"> <strong>Sky</strong>Scraper </a>
            </h1>
          </v-toolbar-title>
        </v-flex>
        <v-flex
shrink fill-height
hidden-sm-and-down
>
          <v-toolbar-items
            v-if="$route.path == '/'"
            id="toolbar-menu"
            class="d-flex"
            justify-end
          >
            <v-btn
flat aria-label="Preview"
to="/demo"
>
              <n-link
to="/demo" style="text-decoration: none;"
>
                Preview
              </n-link>
            </v-btn>
          </v-toolbar-items>
        </v-flex>
      </v-layout>
    </v-toolbar>
    <nuxt />
    <Footer />
  </v-app>
</template>

<script lang="ts">
  import { Component, Vue } from "nuxt-property-decorator";
  import Footer from "~/components/Footer.vue";
  import "vuetify/src/stylus/app.styl";

  interface ISlide {
    id: string;
    name?: string;
    visible: boolean;
    active: boolean;
  }

  @Component({
    data() {
      return {
        drawer: null,
      };
    },
    components: {
      Footer,
    },
  })
  export default class App extends Vue {
    public slides: ISlide[] = [];

    protected mounted() {
      this.$store.commit("SET_NAV_VISIBLE", true);
    }

    get navVisible() {
      return this.$store.getters.NAV_VISIBLE;
    }
  }
</script>

<style lang="scss">
  .v-toolbar__title {
    a {
      &:active {
        color: #f44336 !important;
      }

      color: #f44336 !important;
      text-decoration: none !important;
    }
  }

  #toolbar-menu {
    .active {
      position: relative;

      &::before {
        background-color: currentColor;
      }
    }
  }
</style>
