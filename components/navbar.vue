<script setup lang="ts">
const colorMode = useColorMode();

const switchColors = () => {
  let target = "dark";
  const color = colorMode.value;
  if (color === "dark") {
    target = "light";
  }

  colorMode.preference = target;
  colorMode.value = target;
};
</script>
<template>
  <div class="flex bg-white bg-opacity-5 py-8 w-full">
    <div class="w-11/12 flex flex-row mx-auto justify-between">
      <div class="">
        <NuxtLink class="text-xl" to="/">developer-creations</NuxtLink>
      </div>
      <div v-if="colorMode.value === 'light'" class="text-xl">
        <Icon
          class="cursor-pointer"
          @click="switchColors()"
          name="solar:moon-broken"
        />
      </div>
      <div v-else class="text-xl">
        <Icon
          class="cursor-pointer"
          @click="switchColors()"
          name="solar:sun-broken"
        />
      </div>
    </div>
  </div>
</template>
