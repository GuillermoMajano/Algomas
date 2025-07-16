

<template>
  <div class="bg-slate-50">
    <Header />
    <main>
      <HeroSection />
      <Pilar1Tecnico />
      <Pilar2Entrenamiento />
      <Pilar3Psicologia />
      <Pilar4Ecosistema />
      <Pilar5Dedicacion />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
import Pilar1Tecnico from './components/Pilar1Tecnico.vue'
import Pilar2Entrenamiento from './components/Pilar2Tecnico.vue'
import Pilar3Psicologia from './components/Pilar3Tecnico.vue'
import Pilar4Ecosistema from './components/Pilar4Tecnico.vue'
import Pilar5Dedicacion from './components/Pilar5Tecnico.vue'
import Footer from './components/Footer.vue'
</script>