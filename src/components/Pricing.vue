/* eslint-disable */
<template>
  <div
    class="grid md:grid-cols-3 sm:grid-cols-2 grid-cols-1 xl:mx-52 lg:mx-40 md:mx-32 sm:mx-24 mx-8 mt-12 sm:gap-8 gap-5"
  >
    <template v-for="(pricing, idx) in cards">
      <pricing-card :key="idx" :pricing="pricing" />
    </template>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import PricingCard from "./PricingCard.vue";

export default Vue.extend({
  name: "Pricing",
  components: { PricingCard },
  data: () => ({
    cards: [
      {
        type: "Personal",
        title: "Basic",
        price: 175,
        time: "monthly",
        currency: "€",
        description: "Suitable for personal use",
        recommended: false,
      },
      {
        type: "Teams",
        title: "Business",
        price: 250,
        time: "monthly",
        currency: "€",
        description: "When you're ready to invite people to your office ",
        recommended: true,
      },
      {
        type: "Enterprise",
        title: "Pro",
        price: 725,
        currency: "€",
        description:
          "Pay for this subscription, you have 500 people working with you ",
        recommended: false,
      },
    ],
  }),
});
</script>
