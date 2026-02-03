<template>
  <div class="min-h-screen py-8 px-4">
    <!-- Header -->
    <header class="text-center mb-12 animate-fade-in">
      <h1 class="text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-purple-600 mb-4">
        🎓 English Vocabulary
      </h1>
      <p class="text-gray-600 text-lg max-w-2xl mx-auto">
        Expanda seu vocabulário em inglês de forma interativa! Descubra novas palavras, suas definições e exemplos práticos de uso.
      </p>
    </header>

    <!-- Main Content -->
    <main class="max-w-6xl mx-auto">
      <!-- Controls -->
      <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mb-8">
        <button 
          @click="fetchWords" 
          :disabled="loading"
          class="btn-primary flex items-center gap-2"
        >
          <svg v-if="!loading" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
          </svg>
          <svg v-else class="animate-spin w-5 h-5" fill="none" viewBox="0 0 24 24">
            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
            <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
          </svg>
          {{ loading ? 'Carregando...' : 'Buscar Novas Palavras' }}
        </button>

        <div class="flex items-center gap-2 text-gray-600">
          <span class="text-sm font-medium">Total de palavras:</span>
          <span class="badge">{{ words.length }}</span>
        </div>
      </div>

      <!-- Error/Warning Message -->
      <div v-if="error" class="max-w-2xl mx-auto mb-8 bg-yellow-50 border-l-4 border-yellow-500 p-4 rounded-lg animate-slide-up">
        <div class="flex items-center">
          <svg class="w-6 h-6 text-yellow-500 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
          </svg>
          <div>
            <h3 class="text-yellow-800 font-semibold">Aviso</h3>
            <p class="text-yellow-600 text-sm">{{ error }}</p>
          </div>
        </div>
      </div>

      <!-- Loading State -->
      <div v-if="loading && words.length === 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="n in 6" :key="n" class="card animate-pulse">
          <div class="h-6 bg-gray-200 rounded w-3/4 mb-4"></div>
          <div class="h-4 bg-gray-200 rounded w-full mb-2"></div>
          <div class="h-4 bg-gray-200 rounded w-5/6 mb-4"></div>
          <div class="h-4 bg-gray-200 rounded w-full"></div>
        </div>
      </div>

      <!-- Words Grid -->
      <div v-else-if="words.length > 0" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <WordCard 
          v-for="(word, index) in words" 
          :key="index"
          :word="word"
          :index="index"
        />
      </div>

      <!-- Empty State -->
      <div v-else class="text-center py-16">
        <svg class="w-24 h-24 mx-auto text-gray-300 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
        </svg>
        <h3 class="text-2xl font-semibold text-gray-600 mb-2">Nenhuma palavra ainda</h3>
        <p class="text-gray-500 mb-6">Clique no botão acima para carregar palavras novas!</p>
      </div>
    </main>

    <!-- Footer -->
    <footer class="text-center mt-16 pb-8">
      <p class="text-gray-500 text-sm">
        Desenvolvido para FIAP - Front-end Engineering 🚀
      </p>
      <p class="text-gray-400 text-xs mt-2">
        Consumindo API: 
        <a href="https://fiap-bff-9aojr.onrender.com/ask" 
           target="_blank" 
           class="text-blue-500 hover:text-blue-600 underline">
          FIAP BFF
        </a>
      </p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import WordCard from './components/WordCard.vue'

const words = ref([])
const loading = ref(false)
const error = ref(null)

const API_URL = 'https://fiap-bff-9aojr.onrender.com/ask'

// Dados de fallback caso a API esteja indisponível
const mockWords = [
  {
    word: "Serendipity",
    description: "The occurrence of events by chance in a happy or beneficial way.",
    useCase: "Finding a $20 bill in an old jacket was pure serendipity."
  },
  {
    word: "Eloquent",
    description: "Fluent or persuasive in speaking or writing.",
    useCase: "The speaker gave an eloquent presentation that moved the audience."
  },
  {
    word: "Resilience",
    description: "The capacity to recover quickly from difficulties; toughness.",
    useCase: "Her resilience helped her overcome many challenges in life."
  },
  {
    word: "Ephemeral",
    description: "Lasting for a very short time; transitory.",
    useCase: "The beauty of cherry blossoms is ephemeral, lasting only a few weeks."
  },
  {
    word: "Ubiquitous",
    description: "Present, appearing, or found everywhere.",
    useCase: "Smartphones have become ubiquitous in modern society."
  },
  {
    word: "Paradigm",
    description: "A typical example or pattern of something; a model.",
    useCase: "The internet has created a new paradigm for communication."
  }
]

const fetchWords = async () => {
  loading.value = true
  error.value = null
  
  try {
    const response = await fetch(API_URL)
    
    if (!response.ok) {
      throw new Error(`Erro HTTP: ${response.status}`)
    }
    
    const data = await response.json()
    
    // Verifica se a API retornou erro
    if (data.error) {
      throw new Error('API temporariamente indisponível')
    }
    
    // Adiciona novas palavras sem duplicar
    const newWords = Array.isArray(data) ? data : []
    
    if (newWords.length === 0) {
      throw new Error('API não retornou palavras')
    }
    
    words.value = [...words.value, ...newWords]
    
  } catch (err) {
    console.warn('⚠️ API indisponível, usando dados de exemplo:', err.message)
    
    // Usa dados mockados como fallback
    const randomMockWords = mockWords
      .sort(() => Math.random() - 0.5)
      .slice(0, 3)
    
    words.value = [...words.value, ...randomMockWords]
    
    // Mostra um aviso mais amigável
    error.value = '⚠️ API temporariamente indisponível. Exibindo palavras de exemplo.'
    
    // Remove o erro após 5 segundos
    setTimeout(() => {
      error.value = null
    }, 5000)
  } finally {
    loading.value = false
  }
}

// Carrega palavras iniciais ao montar o componente
fetchWords()
</script>
