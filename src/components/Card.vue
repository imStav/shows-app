<script setup>
const { image, name, location } = defineProps(["image", "name", "location"]);
</script>

<template>
  <div class="n-card">
    <Suspense>
      <template #default>
        <img :src="image" />
      </template>

      <template #fallback>
        <n-spin size="large" />
      </template>
    </Suspense>

    <div class="n-card_decription">
      <h3>{{ name }}</h3>
      <p>{{ location }}</p>
    </div>
  </div>
</template>

<style scoped>
/* Card Styles */
.n-card {
  display: flex;
  flex-direction: row;
  gap: 2rem;
  background-color: #15171d;
  color: #bac5d4;
  padding: 1rem 1rem;
  border-radius: 10px;
}
.n-card img {
  width: 33%;
  height: fit-content;
  align-self: center;
  border-radius: 1000px;
}

.n-card_decription {
  width: 66%;
  justify-self: flex-start;
  align-self: center;
  line-height: .9rem;
}

@media (prefers-color-scheme: dark) {
  .n-card {
    border-color: #2a2e38;
  }
}
</style>
