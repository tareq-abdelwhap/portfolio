<script lang="ts" setup>
const PortfolioStore = usePortfolioStore();
const { skills } = storeToRefs(PortfolioStore);
</script>

<template>
  <div class="w-full">
    <div
      v-for="level_01 in skills"
      :key="level_01.name"
      class="border-b pb-8 mb-8 border-slate-700 w-full"
    >
      <h2
        class="text-4xl font-bold my-8 text-start"
        v-motion
        :initial="{ opacity: 0, x: -70 }"
        :enter="{ opacity: 1, x: 0, transition: { duration: 800 } }"
      >
        {{ level_01.name }}
      </h2>
      <div class="grid grid-cols-5 gap-5 gap-y-12 w-full">
        <div
          v-for="(skill, index) in level_01.skills.filter(s => s.show)"
          :key="skill.name"
          :class="[
            `relative px-4 py-2 rounded-2xl bg-transparent content-center border ${skill.borderColor}`,
          ]"
          v-motion
          :initial="{ opacity: 0, y: 70 }"
          :enter="{
            opacity: 1,
            y: 0,
            transition: { duration: 800, delay: index * 100 },
          }"
        >
          <div class="absolute inset-0 opacity-50 mix-blend-overlay"></div>
          <div class="relative z-10">
            <Icon
              :name="skill.icon"
              :class="[
                'text-4xl text-white',
                'absolute -top-10',
                'overflow-hidden',
              ]"
            />
            <div class="flex justify-between content-center my-2">
              <h3 class="text-2xl font-semibold text-white">
                {{ skill.name }}
              </h3>
              <p class="self-center text-sm">{{ `${skill.years}` }}</p>
            </div>
            <span
              v-if="skill.new"
              :class="[
                'text-xs font-semibold bg-green-900 px-3 py-1 rounded-full absolute -top-7 right-0',
              ]"
            >
              Learning...
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
