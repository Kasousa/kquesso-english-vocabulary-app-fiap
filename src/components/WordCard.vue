<template>
  <div class="card animate-slide-up hover:border-2 hover:border-blue-200" :style="{ animationDelay: `${index * 0.1}s` }">
    <!-- Word Header -->
    <div class="flex items-start justify-between mb-4">
      <h2 class="text-2xl font-bold text-gray-800 flex-1">
        {{ word.word }}
      </h2>
      <button 
        @click="toggleFavorite"
        class="text-2xl transition-transform hover:scale-110 active:scale-95"
        :title="isFavorite ? 'Remover dos favoritos' : 'Adicionar aos favoritos'"
      >
        {{ isFavorite ? '⭐' : '☆' }}
      </button>
    </div>

    <!-- Description -->
    <div class="mb-4">
      <h3 class="text-sm font-semibold text-gray-500 uppercase tracking-wide mb-2 flex items-center gap-2">
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
        Definição
      </h3>
      <p class="text-gray-700 leading-relaxed">
        {{ word.description }}
      </p>
    </div>

    <!-- Use Case -->
    <div class="bg-gradient-to-r from-blue-50 to-indigo-50 rounded-lg p-4 border-l-4 border-blue-500">
      <h3 class="text-sm font-semibold text-gray-500 uppercase tracking-wide mb-2 flex items-center gap-2">
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z" />
        </svg>
        Exemplo de Uso
      </h3>
      <p class="text-gray-700 italic leading-relaxed">
        "{{ word.useCase }}"
      </p>
    </div>

    <!-- Action Buttons -->
    <div class="flex gap-2 mt-4">
      <button 
        @click="speakWord"
        class="flex-1 bg-blue-100 text-blue-700 py-2 px-4 rounded-lg hover:bg-blue-200 transition-colors text-sm font-medium flex items-center justify-center gap-2"
        title="Ouvir pronúncia"
      >
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z" />
        </svg>
        Ouvir
      </button>
      
      <button 
        @click="copyWord"
        class="flex-1 bg-green-100 text-green-700 py-2 px-4 rounded-lg hover:bg-green-200 transition-colors text-sm font-medium flex items-center justify-center gap-2"
        :title="copied ? 'Copiado!' : 'Copiar palavra'"
      >
        <svg v-if="!copied" class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z" />
        </svg>
        <svg v-else class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
        </svg>
        {{ copied ? 'Copiado!' : 'Copiar' }}
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps({
  word: {
    type: Object,
    required: true
  },
  index: {
    type: Number,
    default: 0
  }
})

const isFavorite = ref(false)
const copied = ref(false)

const toggleFavorite = () => {
  isFavorite.value = !isFavorite.value
}

const speakWord = () => {
  if ('speechSynthesis' in window) {
    const utterance = new SpeechSynthesisUtterance(props.word.word)
    utterance.lang = 'en-US'
    utterance.rate = 0.8
    window.speechSynthesis.speak(utterance)
  } else {
    alert('Seu navegador não suporta síntese de voz.')
  }
}

const copyWord = async () => {
  try {
    await navigator.clipboard.writeText(props.word.word)
    copied.value = true
    setTimeout(() => {
      copied.value = false
    }, 2000)
  } catch (err) {
    console.error('Erro ao copiar:', err)
  }
}
</script>
