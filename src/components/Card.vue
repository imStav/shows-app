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
  width: max-content;
  justify-self: flex-start;
  align-self: center;
  line-height: .9rem;
}

.n-card_decription h3 {
  margin-bottom: -.4rem;
}

@media (prefers-color-scheme: dark) {
  .n-card {
    background-color: #15171d;
    color: #bac5d4;
  }
}

@media (prefers-color-scheme: light) {
  .n-card {
    background-color: #eef2fe;
    color: #212935;
  }
}
</style>
