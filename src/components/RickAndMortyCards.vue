<script setup>
import { ref, watch } from "vue";
import axios from "axios";
import Card from "./Card.vue";

const characters = ref(null);
const page = ref(0);

const response = await axios.get(
  `https://rickandmortyapi.com/api/character/?page=${page.value}`
);

characters.value = response.data.results;

console.log(characters.value);

watch(page, async () => {
  const res = await axios.get(
    `https://rickandmortyapi.com/api/character/?page=${page.value + 1}`
  );

  characters.value = res.data.results;
  // console.log(characters.value)
});
</script>

<template>
  <div class="container">
    <div class="cards">
      <TransitionGroup name="fade">
        <Card
            v-for="character in characters"
            :key="character.id"
            :image="character.image"
            :name="character.name"
            :location="character.location.name" 
        />
      </TransitionGroup>
    </div>
  </div>

  <div class="fixed">
    <div class="btns">
      <n-button
        strong
        secondary
        round
        type="primary"
        v-if="page >= 1"
        @click="page = page - 1"
        >Back</n-button
      >
      <n-button strong secondary round type="primary" @click="page = page + 1"
        >Next</n-button
      >
    </div>
  </div>
</template>

<style scoped>
.container {
    margin-top: 3rem;
    margin-bottom: 8rem;
}

.cards {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
    width: 70%;
    margin-inline: auto;
}

.fixed {
  position: fixed;
  bottom: 0;
  width: 100%;
  padding-block: 1rem;
  backdrop-filter: blur(10px);
}

.btns {
  display: flex;
  justify-content: center;
  align-items: center;
}

.btns button {
  margin-inline: 0.3rem;
}

.fade-enter-from, 
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active, 
.fade-leave-active,
.fade-move {
  transition: all 0.2s ease;
  transform: scale(.9);
}

@media screen and (max-width: 760px) {
    .cards {
        width: 80%;
        grid-template-columns: repeat(1, 1fr);
    }
}

@media screen and (min-width: 1000px) {
    .cards {
        width: 33%;
    }
}

@media (prefers-color-scheme: dark) {
  .fixed {
    background-color: #00000091;
  }
}

@media (prefers-color-scheme: light) {
  .fixed {
    background-color: #ffffff91;
  }
}
</style>
