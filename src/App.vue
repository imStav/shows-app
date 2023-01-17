<script setup>
import RickAndMortyCards from "./components/RickAndMortyCards.vue";
</script>

<template>
  <main>
    <div class="heading">
      <h1>Find a character</h1>
    </div>

    <Suspense>
      <template #default>
        <RickAndMortyCards />
      </template>

      <template #fallback>
        <div>
          <p>Loading...</p>
        </div>
      </template>
    </Suspense>
  </main>
</template>

<style scoped>
.heading {
  margin-inline: auto;
  width: fit-content;
}
</style>