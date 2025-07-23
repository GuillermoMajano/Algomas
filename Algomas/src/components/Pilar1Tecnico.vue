<template>
  <section id="pilar1" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-12">Dominio Técnico Fundamental</h2>
      <div  class="grid md:grid-cols-2 lg:grid-cols-3 gap-6" >
        <div v-for="(group, index) in algorithmsData" :key="index" class="expandable algo-card bg-white rounded-lg shadow-md border border-transparent hover:border-teal-500 cursor-pointer"  tabindex="0" aria-expanded="false">
          <div class="p-6">
            <h3 class="font-bold text-lg text-teal-700">{{ group.category }}</h3>
          </div>
          <div class="expandable-content algo-card-details bg-slate-50 px-6">
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

document.querySelectorAll('.expandable').forEach(el => {
  el.addEventListener('click', function () {
    const isExpanded = this.classList.contains('expanded');
    const content = this.querySelector('.expandable-content');

    // Alternar clase
    this.classList.toggle('expanded');

    // Actualizar atributo ARIA
    this.setAttribute('aria-expanded', !isExpanded);

    // Opcional: cambiar el texto del encabezado
    const firstParagraph = this.querySelector('p');
    if (firstParagraph) {
      firstParagraph.textContent = !isExpanded 
        ? 'Haz clic para ocultar' 
        : 'Haz clic aquí para ver más';
    }
  });
});

const algorithmsData = [
  {
    category: 'Estructuras de Datos Fundamentales',
    items: [
      { name: 'Arrays, Listas', desc: 'Almacenamiento secuencial de elementos.', complexity: 'O(1) acceso (array)', space: 'O(N)' },
      { name: 'Árboles Binarios de Búsqueda (BST)', desc: 'Almacenamiento ordenado para búsqueda rápida.', complexity: 'O(log N) promedio', space: 'O(N)' },
      { name: 'Tablas Hash (Hash Maps)', desc: 'Mapeo de claves a valores para acceso casi constante.', complexity: 'O(1) promedio', space: 'O(N)' }
    ]
  },{
    category: 'Búsqueda y Ordenamiento',
    items: [
      { name: 'Merge Sort, Quick Sort', desc: 'Ordenar eficientemente colecciones de datos.', complexity: 'O(N log N)', space: 'O(N) / O(log N)' }
    ]},
  {
    category: 'Algoritmos de Búsqueda en Grafos',
                    items: [
                        { name: 'BFS (Breadth-First Search)', desc: 'Recorrido por niveles, camino más corto.', complexity: 'O(V+E)', space: 'O(V)' },
                        { name: 'DFS (Depth-First Search)', desc: 'Recorrido en profundidad, detección de ciclos.', complexity: 'O(V+E)', space: 'O(V)' },
                        { name: 'Algoritmo de Dijkstra', desc: 'Camino más corto en grafos con pesos no negativos.', complexity: 'O(E log V)', space: 'O(V+E)' }
                    ]
                } ,
    {
                    category: 'Programación Dinámica',
                    items: [
                        { name: 'Problema de la Mochila', desc: 'Optimización de la selección de elementos con restricciones.', complexity: 'O(N*W)', space: 'O(N*W)' },
                        { name: 'Longest Common Subsequence (LCS)', desc: 'Encontrar la secuencia común más larga.', complexity: 'O(N*M)', space: 'O(N*M)' }
                    ]
                },
                 {
                    category: 'Algoritmos de Cadenas',
                    items: [
                        { name: 'KMP (Knuth-Morris-Pratt)', desc: 'Búsqueda eficiente de patrones en texto.', complexity: 'O(N+M)', space: 'O(M)' }
                    ]
                },
                {
                    category: 'Teoría de Números',
                    items: [
                        { name: 'Criba de Eratóstenes', desc: 'Encontrar todos los números primos hasta un límite.', complexity: 'O(N log log N)', space: 'O(N)' }
                ]
                },
                {
                    category: 'Algoritmos de Geometría Computacional',
                    items: [
                        { name: 'Convex Hull', desc: 'Encontrar el envolvente convexo de un conjunto de puntos.', complexity: 'O(N log N)', space: 'O(N)' }
                    ]
                }
]
</script>

<style>
.expandable {
  width: 100%;
  max-width: 500px;
  margin: 1rem auto;
  border: 1px solid #ddd;
  border-radius: 8px;
  cursor: pointer;
  background-color: #f8f9fa;
  padding: 1rem;
  user-select: none;
}

.expandable:hover {
  background-color: #edf0f3;
}

/* Contenido que se despliega */
.expandable-content {
  height: 0;
  overflow: hidden;
  transition: height 0.4s ease-out;
  padding: 0 1rem;
}

/* Estado expandido */
.expandable.expanded .expandable-content {
  height: auto;
  padding: 1rem 1rem;
}

/* Opcional: cambiar texto o estilo cuando está expandido */
.expandable:not(.expanded) .expandable-content {
  display: none; /* Mejor UX: evita que se lea en lectores de pantalla si está cerrado */
}


</style>