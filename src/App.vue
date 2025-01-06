<script setup>
import { ref } from 'vue'
import TheHeader from './components/TheHeader.vue'
import TheSkills from './components/TheSkills.vue'
import TheEducation from './components/TheEducation.vue'
import TheExperience from './components/TheExperience.vue'
import TheCertificates from './components/TheCertificates.vue'
import TheCommunity from './components/community.vue'
import TheProjects from './components/TheProjects.vue' 

const currentLang = ref('zh-tw')
const toggleLang = () => {
  currentLang.value = currentLang.value === 'zh-tw' ? 'en' : 'zh-tw'
}

const exportPDF = () => {
  window.print()
}
</script>
<template>
  <div class="min-h-screen bg-gray-900 text-gray-100">
    <!-- 頂部按鈕 - 保持居中設計 -->
    <div class="max-w-2xl mx-auto px-4">
      <div class="flex justify-center gap-4 py-4">
        <button
          @click="toggleLang"
          class="flex items-center px-4 py-2 text-gray-300 hover:text-blue-400 transition-colors duration-200 text-sm"
        >
          {{ currentLang === 'zh-tw' ? 'English' : '中文' }}
        </button>
        <button
          @click="exportPDF"
          class="flex items-center px-4 py-2 text-gray-300 hover:text-blue-400 transition-colors duration-200 text-sm"
        >
          {{ currentLang === 'zh-tw' ? '匯出 PDF' : 'Export PDF' }}
        </button>
      </div>
    </div>

    <div class="max-w-2xl mx-auto px-4 mt-16">
      <div class="space-y-16">
        <TheHeader :lang="currentLang" class="text-center" />
        <TheExperience :lang="currentLang" />
        <TheEducation :lang="currentLang" />
        <TheSkills :lang="currentLang" />
        <!-- <TheProjects :lang="currentLang" /> -->
        <TheCertificates :lang="currentLang" />
        <TheCommunity :lang="currentLang" />
      </div>
    </div>
  </div>
</template>

<style>
@media print {
  .mt-16 {
    margin-top: 4rem;
  }
}
</style>
