<script setup>
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

let timeline = null

onMounted(() => {
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

    <!-- <div
      class="card-one absolute w-[1000px] w-[1000px] top-0 left-0 bg-red-400 flex items-center justify-center text-[80px]"
    >
       <img
        class="w-full h-full object-cover"
        src="https://img.notionusercontent.com/s3/prod-files-secure%2Fbb35ec0e-0895-4ac1-9277-df94454ee371%2F6dbd3ca5-cf29-4b09-b1b8-9b42ad97986c%2Fimage.png/size/w=2000?exp=1755877926&sig=99B-R4rceSX3fOis0CmHcMfnLPYUes89oY4M1wU5lAw&id=2474862c-23c4-817d-914f-fb7d6153cd82&table=block&userId=4bb4c8fd-231b-496c-99f7-ade481a3eb28"

      WWWHHHYYY
    </div> -->

    <div
      class="card-one absolute top-0 left-0 w-[78vw] h-[500px] bg-black text-white rounded-[20px] text-center flex justify-center p-10"
    >
      <span class="absolute top-10 left-10 text-[30px] font-bold"
        >Project 1 - YOLO Defect Tagger</span
      >
      <div div class="flex items-center justify-center h-full gap-10">
        <div class="max-w-[700px] text-left text-white text-sm leading-relaxed">
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
      <span class="absolute top-10 left-10 text-[30px] font-bold">
        Project 2 – GateBoard system
      </span>

      <div class="flex items-center justify-center h-full gap-10">
        <img
          class="h-[300px] rounded shadow object-cover"
          src="https://images.plurk.com/7LtF2MAbvittoknj1FKOVr.png"
          alt="GateBoard Dashboard"
        />

        <div class="flex flex-col justify-center h-full gap-4 max-w-[600px]">
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
      <span class="absolute top-10 left-10 text-[30px] font-bold">
        Project 3 - HealthCare APP
      </span>

      <div class="flex items-center justify-center h-full gap-10">
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
      <span class="absolute top-10 left-10 text-[30px] font-bold">Project 4 - bird-bird-999</span>
      <div div class="flex items-center justify-center h-full gap-10">
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
</style>
