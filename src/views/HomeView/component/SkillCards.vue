<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
let mm = gsap.matchMedia()

const skills = [
  'Vue 3',
  'React',
  'GSAP',
  'Bootstrap',
  'TypeScript',
  'React Native',
  'Electron',
  'JavaScript',
  'HTML',
  'CSS',
  'Figma',
  'JIRA',
  'Git',
  'Webpack',
  'Firebase',
]

onMounted(() => {
  mm.add('(min-width: 700px)', () => {
    const timeline = gsap.timeline({
      scrollTrigger: {
        trigger: '.skill-title',
        start: 'top 90%',
        scrub: 1,
      },
    })

    timeline
      .from('.skill-title', {
        xPercent: -100,
        duration: 0.8,
        ease: 'power2.out',
      })
      .from(
        '.skills-wrapper',
        {
          xPercent: 100,
          duration: 0.8,
          ease: 'power2.out',
        },
        '-=0.5',
      )
  })

  // 首次的卡片旋轉
  ScrollTrigger.batch('.skill-card', {
    onEnter: (targets) => {
      gsap.fromTo(
        targets,
        {
          opacity: 0,
          rotationY: -90,
          transformPerspective: 800,
        },
        {
          opacity: 1,
          rotationY: 0,
          duration: 1,
          ease: 'back.out(1.4)',
          stagger: 0.15,
        },
      )
    },
    start: 'top 85%',
  })

  gsap.utils.toArray('.skill-card').forEach((card) => {
    gsap.to(card, {
      opacity: 1,
      scrollTrigger: {
        trigger: card,
        start: 'top 85%',
        end: 'top 40%',
        scrub: true,
      },
    })
  })
})
</script>

<template>
  <h1 class="skill-title">Skills</h1>
  <section class="skills-wrapper">
    <div class="skills-grid">
      <div class="skill-card" v-for="(skill, index) in skills" :key="index">
        {{ skill }}
      </div>
    </div>
  </section>
</template>
<style scoped>
.skill-title {
  text-align: center;
  font-size: 50px;
}
.skills-wrapper {
  overflow: hidden;
  position: relative;
  background: #f5f5f5;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 120vh;
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
  max-width: 800px;
  width: 100%;
}
.skills-track {
  gap: 20px;
  padding: 20px;
}

.skill-card {
  min-width: 200px;
  height: 100px;
  background: #fff;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 18px;
  font-weight: bold;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  opacity: 0;
  transform-style: preserve-3d;
  backface-visibility: hidden;
  will-change: transform, opacity;
}
@media (max-width: 700px) {
  .skill-title {
    font-size: 30px;
  }
  .skills-wrapper {
    height: auto;
    background: #f5f5f5;
    padding: 10px;
  }
  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
    max-width: 300px;
    margin: 0 auto;
  }
  .skill-card {
    min-width: auto;
    height: 72px;
    font-size: 16px;
    opacity: 0;
  }
}
</style>
