<script setup>
import { onMounted, onBeforeUnmount } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

let timeline = null
let mm = gsap.matchMedia()

onMounted(() => {
  mm.add('(min-width: 700px)', () => {
    timeline = gsap.timeline({
      scrollTrigger: {
        trigger: '.card-box',
        start: 'top 50px',
        end: '+=1500',
        scrub: true,
        pin: true,
        anticipatePin: 1,
      },
    })

    timeline
      .from('.card-title', { yPercent: 100 })
      .to('.card-title', {
        width: '78vw',
        duration: 0.5,
        ease: 'power2.out',
      })
      .from('.card-one', { xPercent: -100 })
      .from('.card-two', { xPercent: 102 })
      .from('.card-three', { yPercent: -100 })
      .from('.card-four', { yPercent: 100, autoAlpha: 0 })
  })

  mm.add('(max-width: 700px)', () => {
    timeline = gsap.timeline({
      scrollTrigger: {
        trigger: '.card-box',
        start: 'top center',
        end: '+=1500',
        scrub: true,
        anticipatePin: 1,
      },
    })
    timeline
      .from('.card-one', { xPercent: -110 })
      .from('.card-two', { xPercent: 110 })
      .from('.card-three', { xPercent: -110 })
      .from('.card-four', { xPercent: 110, autoAlpha: 0 })
  })
})
onBeforeUnmount(() => mm?.revert())
</script>
<template>
  <div
    class="card-box relative h-[1000px] w-[1000px] flex items-center justify-center overflow-hidden"
  >
    <div
      class="card-title absolute top-0 left-0 text-[50px] text-center h-[500px] w-[0px] border-4 border-black rounded-[20px] leading-[500px]"
    >
      Projects
    </div>

    <div
      class="card-one absolute top-0 left-0 w-[78vw] h-[500px] bg-black text-white rounded-[20px] text-center flex justify-center p-10"
    >
      <div class="progect-name absolute top-10 left-10 text-[30px] font-bold">
        Project 1 - YOLO Defect Tagger
      </div>
      <div div class="card-content flex items-center justify-center h-full gap-10">
        <div class="card-word max-w-[700px] text-left text-white text-sm leading-relaxed">
          Electron + Vue3 desktop app for industrial image labeling, integrating YOLO coordinates,
          canvas operations, and MVVM architecture.
        </div>
        <img
          class="h-[300px] object-cover"
          src="https://images.plurk.com/4k9u4Fc4atT5q9YTSombl2.gif"
        />
      </div>
    </div>

    <div
      class="card-two absolute top-0 left-0 w-[78vw] h-[500px] bg-zinc-900 text-white rounded-[20px] p-10"
    >
      <div class="progect-name absolute top-10 left-10 text-[30px] font-bold">
        Project 2 – GateBoard system
      </div>

      <div class="card-content flex items-center justify-center h-full gap-10">
        <img
          class="h-[300px] rounded shadow object-cover"
          src="https://images.plurk.com/7LtF2MAbvittoknj1FKOVr.png"
          alt="GateBoard Dashboard"
        />

        <div class="card-word flex flex-col justify-center h-full gap-4 max-w-[600px]">
          <p class="text-left text-sm leading-relaxed">
            A factory floor dashboard system for door manufacturing, combining real-time production
            tracking, WebView-based work reporting, multilingual support, and GPT-assisted voice
            input parsing.
          </p>
        </div>
      </div>
    </div>

    <div
      class="card-three absolute top-0 left-0 w-[78vw] h-[500px] bg-gray-400 text-white rounded-[20px] p-10"
    >
      <div class="progect-name absolute top-10 left-10 text-[30px] font-bold">
        Project 3 - HealthCare APP
      </div>

      <div class="card-content health flex items-center justify-center h-full gap-10">
        <img
          class="h-[300px] rounded shadow object-cover"
          src="https://images.plurk.com/66M3toSH3mmYHJZtnir1H1.png"
        />
        <img
          class="h-[300px] rounded shadow object-cover"
          src="https://images.plurk.com/UTVjhJ11RwhhtKE26FtCx.png"
        />

        <div class="flex flex-col justify-center h-full gap-4 max-w-[600px]">
          <p class="text-left text-sm leading-relaxed">
            A mobile app for monitoring indoor health environments with real-time IoT device
            integration. Refactored and redesigned from a legacy React Native codebase, supporting
            multi-language layouts, refresh token-based notifications, and dual-platform
            (iOS/Android) builds.
          </p>
        </div>
      </div>
    </div>

    <div
      class="card-four absolute top-0 left-0 w-[78vw] h-[500px] rounded-[20px] bg-white text-center flex justify-center p-10"
    >
      <div class="progect-name absolute top-10 left-10 text-[30px] font-bold">
        Project 4 - bird-bird-999
      </div>
      <div div class="card-content flex items-center justify-center h-full gap-10">
        <div class="max-w-[700px] text-left text-sm leading-relaxed">
          A birdwatching web app for exploring species in Taiwan, featuring photo uploads, location
          tagging via Google Maps, seasonal hotspot search via eBird API, and a playful avatar
          editor using canvas.
          <div class="block mt-10">
            <a
              class="underline bg-gray-200 h-[50px] mr-10 p-5 text-[16px] rounded-[20px] hover:bg-gray-300"
              href="https://bird-bird-999.web.app/"
              target="_blank"
              >𓄿 Live Site</a
            >
            <a
              class="underline bg-gray-200 h-[50px] p-5 text-[16px] rounded-[20px] hover:bg-gray-300"
              href="https://github.com/zabeth16/bird-bird-999"
              target="_blank"
              >𒀭 GitHub</a
            >
          </div>
        </div>

        <img
          class="h-[250px] object-cover rounded-[20px]"
          src="https://images.plurk.com/1RwVhHaf81Bv4gikpXXwZt.png"
        />
      </div>
    </div>
  </div>
</template>
<style scoped>
.card-two {
  background-color: #2b2b2b;
}
@media (max-width: 700px) {
  .card-box {
    position: relative;
    width: 100%;
    max-width: 100%;
    height: auto;
    padding: 16px;
    overflow: visible;
    flex-direction: column;
  }

  .card-title {
    position: static;
    width: 100%;
    height: auto;
    line-height: 1.2;
    padding: 12px 16px;
    margin-bottom: 12px;
    font-size: 28px;
    border-width: 2px;
  }

  .progect-name {
    position: static;
    width: 100%;
    text-align: center;
    font-size: 20px;
  }

  .card-one,
  .card-two,
  .card-three,
  .card-four {
    position: static;
    width: 350px;
    height: auto;
    margin: 16px 0;
    padding: 16px;
    display: block;
  }
  .card-content {
    flex-direction: column;
    padding: 10px;
    text-align: center;
  }
  .card-content.health {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
    text-align: left;
  }
  .card-word {
    width: 300px;
    height: auto;
  }

  /* 圖片全寬、有限高 */
  .card-one img,
  .card-two img,
  .card-three img,
  .card-four img {
    max-height: 220px;
    height: auto;
    object-fit: cover;
  }
}
</style>
