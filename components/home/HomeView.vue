<template>
  <v-container
fluid pa-0
ma-0
>
    <v-layout
row wrap
>
      <IntroView />
      <CaptureView />
      <ApplicationsView />
      <PricingView />
      <AboutView />
    </v-layout>
  </v-container>
</template>

<script lang="ts">
  import AboutView from "@/views/AboutView.vue";
  import ApplicationsView from "@/views/ApplicationsView.vue";
  import CaptureView from "@/views/CaptureView.vue";
  import PricingView from "@/views/HardwareView.vue";
  import IntroView from "@/views/IntroView.vue";
  import { Component, Vue } from "nuxt-property-decorator";

  interface ISlide {
    component: Vue;
    id: string;
    name?: string;
    visible: boolean;
    active: boolean;
  }

  @Component({
    components: {
      AboutView,
      PricingView,
      ApplicationsView,
      IntroView,
      CaptureView,
    },
    meta: [
      { name: "og:image", content: "/img/og-banner.png" },
      { name: "canonical", href: "https://skyscraper.ai/", id: "canonical" },
      { name: "viewport", content: "width=device-width, initial-scale=1" },
      {
        name: "description",
        content: `Radios got smarter, computers got faster, and now SkyScraper
      . Meet the Swiss-army knife of radio capture and analysis.`,
      },
      { name: "Content-Type", content: "text/html; charset=utf-8" },
    ],
  })
  export default class HomeView extends Vue {
    public slides: ISlide[] = [];
    protected mounted() {
      this.$store.commit("SET_NAV_VISIBLE", true);
    }
  }
</script>
