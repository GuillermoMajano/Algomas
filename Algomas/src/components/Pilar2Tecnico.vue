<template>
  <section id="pilar2" class="py-20">
    <div class="container mx-auto px-6">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-12">Metodologías de Entrenamiento Riguroso</h2>
      <div class="flex flex-col md:flex-row items-center justify-center gap-4 relative">
        <div v-for="(step, index) in steps" :key="index" class="upsolving-step bg-white p-4 rounded-lg shadow-md text-center w-full md:w-48"
             @mouseenter="showInfo(step.description)" @mouseleave="clearInfo">
          <h4 class="font-bold text-teal-600">{{ step.number }}. {{ step.title }}</h4>
          <p class="text-sm">{{ step.subtitle }}</p>
        </div>
      </div>
      <p class="text-center mt-8 text-slate-600 h-6">{{ infoText }}</p>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const infoText = ref('')

const showInfo = (text) => {
  infoText.value = text
}

const clearInfo = () => {
  infoText.value = ''
}

const steps = [
  { number: 1, title: 'Análisis', subtitle: 'Revisar Concurso', description: 'Se revisan problemas resueltos y no resueltos, identificando dificultades y temas.' },
  { number: 2, title: 'Reintento', subtitle: 'Resolver Problemas', description: 'Se vuelve a intentar resolver los problemas no completados, donde ocurre el mayor aprendizaje.' },
  { number: 3, title: 'Diagnóstico', subtitle: 'Analizar Fallos', description: 'Se examinan críticamente los errores, buscando la raíz del fallo.' },
  { number: 4, title: 'Aprendizaje', subtitle: 'Nuevos Enfoques', description: 'Soluciones de otros para aprender nuevas técnicas.' },
  { number: 5, title: 'Implementación', subtitle: 'Probar y Validar', description: 'Se codifican las nuevas soluciones aprendidas para internalizar el conocimiento.' }
]
</script>