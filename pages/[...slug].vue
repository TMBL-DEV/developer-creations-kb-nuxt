<template>
  <main>
    <ContentDoc :path="$route.path">
      <template v-slot="{ doc }">
        <ContentRenderer :value="doc" />
      </template>
      <template #not-found>
        <div class="flex w-full h-full">
          <h1 class="text-center m-auto">Page not found ☠️</h1>
        </div>
      </template>
    </ContentDoc>
  </main>
</template>
