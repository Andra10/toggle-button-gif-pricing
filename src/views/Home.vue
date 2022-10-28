<template>
  <div class="home" ref="gifBg" id="gifBg">
    <div
      class="container mx-auto pt-40 pb-6 text-center"
      :class="isPlaying ? 'text-white' : 'text-black'"
    >
      <Heading />
      <SubscriptionTypeBtns @changeTime="playOrStopGif" />
      <Pricing />
    </div>
    <footer class="footer">
      <a class="flex" href="https://github.com/Andra10"> source </a>
      <a href="https://portfolio-andra10.vercel.app/#/">about</a>
    </footer>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { mapGetters, mapActions } from "vuex";

import Pricing from "@/components/Pricing.vue";
import Heading from "@/components/Heading.vue";
import SubscriptionTypeBtns from "@/components/SubscriptionTypeBtns.vue";

export default Vue.extend({
  name: "Home",

  components: {
    Pricing,
    Heading,
    SubscriptionTypeBtns,
  },
  computed: {
    ...mapGetters(["isPlaying"]),
  },
  data: () => ({
    gifs: [
      {
        url: "/img/gifs/spit.webp",
        time: 4000,
        implication: "YEAR",
      },
      {
        url: "/img/gifs/p&r.webp",
        time: 3000,
        implication: "YEAR",
      },
      {
        url: "/img/gifs/friends.webp",
        time: 4000,
        implication: "YEAR",
      },
      {
        url: "/img/gifs/owl.webp",
        time: 2500,
        implication: "YEAR",
      },
      {
        url: "/img/gifs/shaking-head.webp",
        time: 3000,
        implication: "MONTH",
      },
      {
        url: "/img/gifs/office.webp",
        time: 2500,
        implication: "MONTH",
      },
      {
        url: "/img/gifs/mr-bean.webp",
        time: 3000,
        implication: "MONTH",
      },
    ],
  }),
  mounted() {
    this.preloadImages();
    this.$store.subscribe((mutation) => {
      if (mutation.type == "stop") {
        this.changeBg("");
      }
    });
  },
  methods: {
    ...mapActions(["playOrStop"]),
    async playOrStopGif(time: string) {
      const filteredGifs = this.gifs.filter((item) => item.implication == time);
      const randomIndex = Math.ceil(Math.random() * filteredGifs.length) - 1;
      const gif = filteredGifs[randomIndex];

      this.changeBg(gif.url);
      await this.$nextTick();
      this.playOrStop(gif);
    },
    changeBg(url: string) {
      const element = document.getElementById("gifBg") as HTMLElement;
      element.style.backgroundImage = `url(${url})`;
    },
    preloadImages() {
      const images = [];
      for (var i = 0; i < this.gifs.length; i++) {
        images[i] = new Image();
        images[i].src = this.gifs[i].url;
        if (images[i].complete) continue;
      }
    },
  },
});
</script>

<style>
.home {
  position: relative;
  height: 100%;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}
.footer {
  position: absolute;
  top: 50px;
  left: 50%;
  transform: translateX(-50%);
}
</style>
