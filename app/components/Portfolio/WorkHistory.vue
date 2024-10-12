<script lang="ts" setup>
const PortfolioStore = usePortfolioStore();
const { experiences } = storeToRefs(PortfolioStore);

callOnce(() => experiences.value.reverse());
</script>

<template>
  <div class="w-full flex flex-wrap gap-y-10">
    <div
      class="grid grid-cols-6 gap-x-5 w-full"
      v-for="(experience, index) in experiences"
      :key="experience.company"
      v-motion
      :initial="{ opacity: 0, x: -30 }"
      :enter="{
        opacity: 1,
        x: 0,
        transition: { duration: 500, delay: index * 100 },
      }"
    >
      <div
        :class="[
          'col-span-1',
          'text-sm text-end border-e border-slate-600 pe-5',
        ]"
      >
        {{ experience.date.join(' - ') }}
      </div>
      <div class="col-span-5">
        <h2 class="text-2xl font-bold">{{ experience.company }}</h2>
        <p>
          {{ experience.position }}
          <span
            v-for="tag in experience.tags"
            :key="tag"
            class="text-xs px-2 py-1 me-2 bg-zinc-700 rounded-full"
          >
            {{ tag }}
          </span>
        </p>
        <ul class="list-disc ps-12">
          <li
            v-for="responsibility in experience.responsibilities"
            :key="responsibility"
          >
            {{ responsibility }}
          </li>
        </ul>
        <span
          v-for="skill in experience.skills"
          :key="skill.name"
          :class="[
            'text-md px-3 me-2 mt-3 inline-block rounded-full border',
            `${skill.borderColor} ${skill.color}`,
          ]"
        >
          {{ skill.name }}
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
