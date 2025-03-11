# src/components/community.vue
<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const community = computed(() => [
    {
        name: 'SITCON 2025 學生計算機年會',
        nameEn: 'SITCON 2025',
        type: '行政組副組長',
        typeEn: 'Deputy Director of the administrative group',
        // issuer: '12',
        // issuerEn: '1212',
        date: '2024'
    },
    {
        name: 'SITCON 2024 學生計算機年會',
        nameEn: 'SITCON',
        type: '場務組組員',
        typeEn: '場務組組員',
        // issuer: '1212',
        // issuerEn: '121212',
        date: '2023'
    },

])

const title = computed(() => props.lang === 'zh-tw' ? '社群參與' : ' Community Engagement')
</script>

<template>
    <section class="mb-12">
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>
        <div class="space-y-8">
            <div v-for="cert in community" :key="cert.name" class="group relative pl-8">
                <!-- 時間軸裝飾 -->
                <div class="absolute left-0 top-0 h-full w-px bg-gray-700 group-hover:bg-blue-500 transition-colors duration-300"
                    :class="{ 'h-3/4': cert === community[community.length - 1] }"></div>
                <div
                    class="absolute left-0 top-2 w-3 h-3 rounded-full border-2 border-gray-700 bg-gray-900 -translate-x-[6px] group-hover:border-blue-500 group-hover:bg-blue-900 transition-colors duration-300">
                </div>

                <div class="Community-card">
                    <div class="mb-2">
                        <h3 class="text-xl font-bold text-white mb-1">
                            {{ props.lang === 'zh-tw' ? cert.name : cert.nameEn }}
                        </h3>
                        <div class="text-blue-400 mb-1">
                            {{ props.lang === 'zh-tw' ? cert.issuer : cert.issuerEn }}
                        </div>
                        <div class="flex items-center text-sm text-gray-400">
                            <span>{{ props.lang === 'zh-tw' ? cert.type : cert.typeEn }}</span>
                            <span class="mx-2">|</span>
                            <span>{{ cert.date }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.Community-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.Community-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>