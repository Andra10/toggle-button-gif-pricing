<template>
  <div
    class="pricing-cards bg-transparent rounded-xl p-5 sm:p-6 md:p-8 lg:p-12"
    :class="
      pricing.recommended
        ? 'border-4 border-blue-400'
        : 'border border-slate-100'
    "
  >
    <div>
      <span class="text-xs font-light">{{ pricing.type }}</span>
    </div>
    <h2 class="font-bold text-3xl">{{ pricing.title }}</h2>

    <div class="font-regular text-xl mt-3 tracking-wide">
      <span>{{ pricing.currency }}</span>
      <span>{{ pricing.price }}</span>
    </div>

    <div class="text-xs opacity-50 mt-2">{{ pricing.description }}</div>

    <div class="flex justify-center align-center">
      <button
        class="text-white hover:shadow-xl elevation=8 bg-blue-500 h-10 rounded-xl transition-shadow duration-200 text-sm px-5 mt-6"
      >
        Buy {{ pricing.title }}
      </button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "PricingCard",
  props: {
    pricing: {
      type: Object,
      default: () => ({}),
      required: true,
    },
  },
});
</script>

<style scoped>
.pricing-cards:hover {
  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px,
    rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px,
    rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
}
</style>
