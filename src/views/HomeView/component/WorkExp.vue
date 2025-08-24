<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)
const mm = gsap.matchMedia()

onMounted(() => {
  gsap.timeline({
    scrollTrigger: {
      trigger: '.container',
      start: 'top top',
      end: '+=200px',
      scrub: true,
      pin: true,
      id: 'container-id',
    },
  })

  mm.add('(min-width: 700px)', () => {
    const boxes = gsap.utils.toArray('.box')
    boxes.forEach((box) => {
      gsap.to(box, {
        x: 300,
        scrollTrigger: {
          trigger: box,
          scrub: true,
          start: 'top 80%',
          toggleActions: 'play none none reverse',
        },
      })
    })
  })
})
</script>
<template>
  <div class="container flex justify-center relative">
    <span class="card-title text-[50px] z-1 bg-white text-center">Work Experience</span>

    <div
      class="track absolute left-0 top-0 translate-x-[-55%] -translate-y-1/5 w-[90vw] h-[90vw] rounded-full border-[2px] border-gray-400 z-0"
    ></div>
  </div>

  <div class="box-container">
    <div class="box">
      <div class="work-title text-[25px]">Front-end Developer • 超數科技 Hyper Data</div>
      <ul class="list-disc">
        <li>
          Developed cross-platform applications and web projects using Vue3, Bootstrap, Electron,
          and React Native.
        </li>
        <li>
          Collaborated closely with back-end engineers, PMs, and clients to clarify requirements and
          deliver implementations that met business needs.
        </li>
      </ul>
      <div class="text-gray text-[20px] mt-5">2024.07~2025.06</div>
    </div>

    <div class="box">
      <div class="work-title text-[25px]">Front-end Developer • 聖勝科技有限公司</div>
      <ul class="list-disc">
        <li>
          Developed and maintained a large-scale internal management platform using React,
          TypeScript, and Ant Design (ANTD), focusing on form data flow and user experience
          optimization.
        </li>
        <li>
          Collaborated closely with back-end engineers, PMs, and overseas teams, communicating in
          both English and Mandarin to ensure accurate implementation of requirements.
        </li>
        <li>
          Proficient in JIRA (project management), GitLab (version control), and Jenkins (CI/CD
          automation).
        </li>
      </ul>
      <div class="text-gray text-[20px] mt-5">2023.06~2024.04</div>
    </div>

    <div class="box">
      <div class="work-title text-[25px]">Full-time Student • WeHelp Bootcamp</div>
      <ul class="list-disc">
        <li>Completed a 6-month intensive full-time web development training program.</li>
        <li>
          Self-learned and implemented projects using HTML, CSS, JavaScript, Python, MySQL, and
          FastAPI.
        </li>
      </ul>
      <div class="text-gray text-[20px] mt-5">2022.09~2023.03</div>
    </div>
  </div>
</template>
<style scoped>
.box {
  margin-bottom: 20vh;
  background-color: rgb(192, 192, 192);
  max-width: 600px;
  border-radius: 20px;
  padding: 30px;
  z-index: 10;
}
@media (max-width: 700px) {
  .card-title {
    font-size: 30px;
  }
  .box-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    width: 100%;
    max-width: 100%;
    flex-direction: column;
  }
  .box {
    margin-bottom: 50px;
    width: 350px;
  }
  .work-title {
    font-size: 25px;
  }
}
</style>
