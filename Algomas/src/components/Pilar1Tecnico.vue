<template>
  <section id="pilar1" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-12">Dominio Técnico Fundamental</h2>
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
        <div v-for="(group, index) in algorithmsData" :key="index" class="algo-card bg-white rounded-lg shadow-md overflow-hidden border border-transparent hover:border-teal-500 cursor-pointer transition-all duration-300">
          <div class="p-6">
            <h3 class="font-bold text-lg text-teal-700">{{ group.category }}</h3>
          </div>
          <div class="algo-card-details bg-slate-50 px-6">
            <ul class="pt-4 pb-6 space-y-3">
              <li v-for="item in group.items" :key="item.name" class="border-l-2 border-teal-200 pl-3">
                <p class="font-semibold text-slate-800">{{ item.name }}</p>
                <p class="text-sm text-slate-600">{{ item.desc }}</p>
                <p class="text-xs text-slate-500 mt-1">Tiempo: {{ item.complexity }} | Espacio: {{ item.space }}</p>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const algorithmsData = [
  {
    category: 'Estructuras de Datos Fundamentales',
    items: [
      { name: 'Arrays, Listas', desc: 'Almacenamiento secuencial de elementos.', complexity: 'O(1) acceso (array)', space: 'O(N)' },
      { name: 'Árboles Binarios de Búsqueda (BST)', desc: 'Almacenamiento ordenado para búsqueda rápida.', complexity: 'O(log N) promedio', space: 'O(N)' },
      { name: 'Tablas Hash (Hash Maps)', desc: 'Mapeo de claves a valores para acceso casi constante.', complexity: 'O(1) promedio', space: 'O(N)' }
    ]
  },
  {
    category: 'Búsqueda y Ordenamiento',
    items: [
      { name: 'Búsqueda Binaria', desc: 'Encontrar un elemento en una lista ordenada.', complexity: 'O(log N)', space: 'O(1)' },
      { name: 'Merge Sort, Quick Sort', desc: 'Ordenar eficientemente colecciones de datos.', complexity: 'O(N log N)', space: 'O(N) / O(log N)' }
    ]
  }
]
</script>