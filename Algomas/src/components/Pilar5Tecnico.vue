<template>
  <section id="pilar5" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <h2 class="text-3xl font-bold text-slate-800 text-center mb-12">Dedicación Inquebrantable y Consistencia</h2>
      <div class="chart-container mx-auto max-w-4xl h-96">
        <canvas ref="chartCanvas"></canvas>
      </div>
      <p class="text-center mt-4 text-sm text-slate-500">Comparativa del número de victorias en competencias importantes.</p>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Chart from 'chart.js/auto'

const chartCanvas = ref(null)

onMounted(() => {
  new Chart(chartCanvas.value, {
    type: 'bar',
    data: {
      labels: ['IOI Gold Medals', 'ICPC World Finals', 'Google Code Jam', 'Topcoder Open', 'Facebook Hacker Cup'],
      datasets: [
        {
          label: 'Gennady Korotkevich',
          data: [6, 2, 8, 4, 5],
          backgroundColor: 'rgba(15, 118, 110, 0.7)',
          borderColor: 'rgba(15, 118, 110, 1)',
          borderWidth: 1
        },
        {
          label: 'Petr Mitrichev',
          data: [2, 2, 1, 4, 3],
          backgroundColor: 'rgba(51, 65, 85, 0.7)',
          borderColor: 'rgba(51, 65, 85, 1)',
          borderWidth: 1
        }
      ]
    },
    options: {
      responsive: true,
      plugins: {
        title: { display: true, text: 'Victorias de Campeones' }
      },
      scales: {
        y: { beginAtZero: true }
      }
    }
  })
})
</script>

<style scoped>
.chart-container {
  height: 400px;
}
</style>