<template>
  <section id="pilar1" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-12">Dominio Técnico Fundamental</h2>
      <div  class="grid md:grid-cols-2 lg:grid-cols-3 gap-6" >
        <div v-for="(group, index) in algorithmsData" :key="index" class="expandable"  tabindex="0"  role="button">
          <div class="p-6 expandable-titulo">
            <h3 class="font-bold text-lg text-teal-700">{{ group.category }}</h3>
          </div>
          <div class="expandable-content algo-card-details bg-slate-50">
            <ul class="pt-4 pb-6 ">
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

// Espera a que el DOM esté completamente cargado antes de ejecutar el script
document.addEventListener('DOMContentLoaded', () => {
    // Selecciona todos los elementos con la clase 'acordeon-item'
    const acordeonItems = document.querySelectorAll('.expandable');

    // Itera sobre cada ítem del acordeón para añadir un event listener
    acordeonItems.forEach(item => {
        // Selecciona el título dentro de cada ítem del acordeón
        const titulo = item.querySelector('.expandable-titulo');

        // Añade un event listener para el evento 'click' al título
        titulo.addEventListener('click', () => {
            // Cierra cualquier otro ítem del acordeón que esté abierto
            acordeonItems.forEach(otherItem => {
                // Si el ítem actual no es el que se clickeó Y tiene la clase 'activo'
                if (otherItem !== item && otherItem.classList.contains('activo')) {
                    // Remueve la clase 'activo' para cerrarlo
                    otherItem.classList.remove('activo');
                    // Restablece el padding del contenido para una transición suave al cerrar
                    otherItem.querySelector('.expandable-content').style.padding = '0px';
                }
            });

            // Alterna la clase 'activo' en el ítem del acordeón que fue clickeado
            // Si tiene 'activo', lo quita; si no lo tiene, lo añade
            item.classList.toggle('activo');

            // Ajusta el padding del contenido del ítem clickeado
            const contenido = item.querySelector('.expandable-content');
            if (item.classList.contains('activo')) {
                // Si el ítem está ahora activo (abierto), aplica el padding
                contenido.style.padding = '15px 0px'; // Coincide con el padding en CSS
            } else {
                // Si el ítem está ahora inactivo (cerrado), quita el padding
                contenido.style.padding = '0px';
            }
        });
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
  width: 90%;
  max-width: 700px;
  margin: 1rem auto;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f8f9fa;

}


.expandable:hover {
  background-color: #edf0f3;
}

/* Contenido que se despliega */
.expandable-content {
  max-height: 100px; /* Comienza colapsado */
  overflow: hidden;
  transition: max-height 0.4s ease-out, padding 0.4s ease-out;
  background-color: #eef7fc;
}

.expandable-content li {
    padding: 12px 25px; /* Padding para los elementos de la lista */
    border-bottom: 1px solid #eef7fc; /* Separador suave para los ítems de la lista */
}


/* Estado expandido */
.expandable.activo .expandable-content {

   max-height: 300px;
  padding: 15px 0px;
}

/* Opcional: cambiar texto o estilo cuando está expandido */


</style>