<script setup>
import RickAndMortyCards from "./components/RickAndMortyCards.vue";
</script>

<template>
  <main>
    <div class="heading">
      <h1>Rick & Morty</h1>
      <p>Find any character of the TV show!</p>
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 2rem;
}

.heading h1 {
  margin-bottom: 0;
}

.heading p {
  font-style: italic;
  margin-top: 0;
}
</style>