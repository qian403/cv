# src/components/TheCertificates.vue
<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const certificates = computed(() => [
    {
        name: '初階資安工程師',
        nameEn: 'CEH (Certified Ethical Hacker)',
        type: '資安證照',
        typeEn: 'Security Certificate',
        issuer: '經濟部產業人才能力鑑定',
        issuerEn: 'Institute for Information Industry',
        date: '2023'
    },
    {
        name: '網路架設乙級',
        nameEn: 'Network Installation Class B Technician',
        type: '技術士證照',
        typeEn: 'Technical Certificate',
        issuer: '勞動部',
        issuerEn: 'Ministry of Labor',
        date: '2023'
    },
    {
        name: '電腦硬體裝修乙級',
        nameEn: 'Computer Hardware Maintenance Class B Technician',
        type: '技術士證照',
        typeEn: 'Technical Certificate',
        issuer: '勞動部',
        issuerEn: 'Ministry of Labor',
        date: '2022'
    }
])

const title = computed(() => props.lang === 'zh-tw' ? '專業證照' : 'Certifications')
</script>

<template>
    <section class="mb-12">
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>
        <div class="space-y-8">
            <div v-for="cert in certificates" :key="cert.name" class="group relative pl-8">
                <!-- 時間軸裝飾 -->
                <div class="absolute left-0 top-0 h-full w-px bg-gray-700 group-hover:bg-blue-500 transition-colors duration-300"
                    :class="{ 'h-3/4': cert === certificates[certificates.length - 1] }"></div>
                <div class="absolute left-0 top-2 w-3 h-3 rounded-full border-2 border-gray-700 bg-gray-900 -translate-x-[6px] group-hover:border-blue-500 group-hover:bg-blue-900 transition-colors duration-300">
                </div>

                <!-- 證照內容 -->
                <div class="certificate-card">
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
.certificate-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.certificate-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>