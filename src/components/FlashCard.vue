<template>
  <div class="w-64 h-80 perspective" @click="flipCard">
    <div
      :class="[
        'w-full h-full transform-style preserve-3d transition-transform duration-700',
        { 'rotate-y-180': flipped },
      ]"
      class="card"
    >
      <div
        class="w-full h-full text-center bg-white p-6 rounded-lg shadow-lg absolute backface-hidden flex flex-col justify-between"
      >
        <h3 class="text-xl text-black font-semibold text-center mb-4">
          {{ frontText }}
        </h3>
        <button
          class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 transition self-center mb-4"
        >
          Mostrar Resposta
        </button>
      </div>

      <div
        class="w-full h-full bg-green-500 p-6 rounded-lg shadow-lg absolute backface-hidden rotate-y-180 flex flex-col justify-between"
      >
        <h3 class="text-xl font-semibold text-center mb-4">{{ backText }}</h3>
        <button
          class="px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600 transition self-center mb-4"
        >
          Voltar
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const frontText = "Qual é a capital da França?";
const backText = "Paris";

const flipped = ref(false);

const flipCard = () => {
  flipped.value = !flipped.value;
};
</script>

<style scoped>
.perspective {
  perspective: 1000px;
}

.card {
  transform-style: preserve-3d;
}

.backface-hidden {
  backface-visibility: hidden;
}

.rotate-y-180 {
  transform: rotateY(180deg);
}
</style>
