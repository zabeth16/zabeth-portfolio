<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import SkillCards from './component/SkillCards.vue'
import ProjectCards from './component/ProjectCards.vue'
import WorkExp from './component/WorkExp.vue'
import ContactMe from './component/ContactMe.vue'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  gsap
    .timeline({
      scrollTrigger: {
        trigger: '.banner-slogan',
        start: 'top center',
        toggleActions: 'play none none reset',
      },
    })
    .from('.name', {
      opacity: 0,
      y: 50,
      duration: 1,
      ease: 'power2.out',
    })
    .from(
      '.identity',
      {
        opacity: 0,
        y: 30,
        duration: 1,
        ease: 'power2.out',
      },
      '-=0.5',
    )
    .from(
      '.scroll-notice',
      {
        opacity: 0,
        y: 80,
        duration: 1,
        ease: 'power2.out',
      },
      '-=1',
    )

  // 淡出
  gsap.to('.banner-slogan', {
    scrollTrigger: {
      trigger: '.banner-slogan',
      start: 'top top',
      end: 'bottom top',
      scrub: 3,
    },
    opacity: 0,
    y: -50,
    ease: 'power2.out',
  })
})
</script>
<template>
  <div class="flex justify-center">
    <div>
      <div class="banner-slogan w-[1000px] h-dvh text-[80px] mt-30 text-center font-bold">
        <h1 class="name">ZABETH Chen</h1>
        <h3 class="identity">Front-end Developer</h3>
        <div class="scroll-notice text-[25px] flex flex-col items-center justify-center">
          <p>Scroll to know more about me</p>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="currentColor"
            class="down-arrow w-6 h-6 animate-bounce mt-5"
          >
            <path
              fill-rule="evenodd"
              d="M11.47 13.28a.75.75 0 0 0 1.06 0l7.5-7.5a.75.75 0 0 0-1.06-1.06L12 11.69 5.03 4.72a.75.75 0 0 0-1.06 1.06l7.5 7.5Z"
              clip-rule="evenodd"
            />
            <path
              fill-rule="evenodd"
              d="M11.47 19.28a.75.75 0 0 0 1.06 0l7.5-7.5a.75.75 0 1 0-1.06-1.06L12 17.69l-6.97-6.97a.75.75 0 0 0-1.06 1.06l7.5 7.5Z"
              clip-rule="evenodd"
            />
          </svg>
        </div>
      </div>
      <SkillCards />
      <ProjectCards />
      <WorkExp />
      <ContactMe />
    </div>
  </div>
</template>
<style scoped>
@media (max-width: 700px) {
  .banner-slogan {
    font-size: 30px;
    height: 500px;
  }
  .scroll-notice {
    font-size: 20px;
  }
}
</style>
