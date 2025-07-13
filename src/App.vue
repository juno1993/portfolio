<template>
  <div id="app-container">
    <Hero />
    <div class="scroll-container">
      <div class="phone-mockup">
        <div class="phone-screen">
          <div class="content-sections">
            <About />
            <Projects />
            <Skills />
            <Contact />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import Hero from './components/Hero.vue';
import About from './components/About.vue';
import Projects from './components/Projects.vue';
import Skills from './components/Skills.vue';
import Contact from './components/Contact.vue';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  const tl = gsap.timeline({
    scrollTrigger: {
      trigger: '.scroll-container',
      start: 'top top',
      end: '+=4000',
      scrub: true,
      pin: true,
    },
  });

  tl.to('.phone-mockup', {
    scale: 1.5,
    duration: 1,
  }).to('.content-sections', {
    yPercent: -75,
    duration: 3,
  });
});
</script>

<style>
#app-container {
  overflow-x: hidden;
}

.scroll-container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.phone-mockup {
  width: 375px;
  height: 812px;
  background: #111;
  border-radius: 40px;
  padding: 20px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  transform: scale(0.5);
}

.phone-screen {
  background: #fff;
  height: 100%;
  border-radius: 20px;
  overflow: hidden;
}

.content-sections {
  height: 400%;
}

section {
  height: 25%;
  padding: 20px;
}
</style>