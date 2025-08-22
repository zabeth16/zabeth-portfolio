<script setup>
function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>
<template>
  <section
    class="w-full h-[50vh] bg-white border-t-2 border-gray-400 rounded-t-full text-center pt-20"
  >
    <h2 class="text-4xl font-bold mb-6">Get In Touch</h2>
    <p class="text-lg mb-4">I'm open to front-end opportunities — feel free to reach out!</p>
    <a
      href="mailto:karta1862025@gmail.com"
      class="text-xl underline hover:text-blue-400 transition-all duration-300"
    >
      karta1862025@gmail.com
    </a>
  </section>
  <button
    @click="scrollToTop"
    class="fixed bottom-6 right-6 bg-black text-white px-4 py-2 rounded-full shadow-md hover:bg-gray-600 cursor-pointer transition-all z-50"
  >
    ↑ Top
  </button>
</template>
<style scoped></style>
