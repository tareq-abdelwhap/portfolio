<script lang="ts" setup>
const PortfolioStore = usePortfolioStore();
const { basic } = storeToRefs(PortfolioStore);
</script>

<template>
  <div class="grid grid-cols-2 h-full">
    <div
      :class="[
        'opacity-0', // for animation
        'col-span-1 text-3xl text-slate-300 text-start self-center ms-20 leading-[70px]',
      ]"
      v-motion
      :initial="{ opacity: 0, x: -70 }"
      :enter="{ opacity: 1, x: 0, transition: { duration: 800 } }"
    >
      <h1 class="text-7xl font-bold">{{ basic.name }}</h1>
      <p>{{ basic.role }}</p>
      <p class="leading-6 text-slate-500 text-xl">{{ basic.description }}</p>
    </div>
    <div class="flex col-span-1 self-end justify-center">
      <img
        :src="basic.me"
        alt="Tareq Abdelwhap"
        ref="img"
        :class="[
          'opacity-0', // for animation
        ]"
        v-motion
        :initial="{ opacity: 0, y: 70 }"
        :enter="{ opacity: 1, y: 0, transition: { duration: 800 } }"
      />
      <div
        class="absolute inset-0 bg-gradient-to-t from-indigo-950 to-transparent to-25%"
      ></div>
    </div>
  </div>
</template>

<style scoped></style>
