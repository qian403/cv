<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const education = computed(() => [
    {
        school: '國立宜蘭大學',
        schoolEn: 'National Yilan University',
        department: '資訊工程學系',
        departmentEn: 'Department of Information Engineering',
        period: '2024 - 現在',
        periodEn: '2024 - Present',
        //description: '專注於資訊安全、網路技術與系統開發',
        descriptionEn: 'Focus on cybersecurity, network technology and system development'
    },
    {
        school: '國立羅東高級工業職業學校',
        schoolEn: 'National Luodong Industrial Vocational High School',
        department: '資訊科',
        departmentEn: 'Department of Information',
        period: '2021 - 2024',
        periodEn: '2021 - 2024',
        //description: '主修資訊技術與程式設計，參與多項技能競賽',
        descriptionEn: 'Major in IT and programming, participated in multiple skill competitions'
    }
])

const title = computed(() => props.lang === 'zh-tw' ? '教育背景' : 'Education')
</script>

<template>
    <section class="mb-12">
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>
        <div class="space-y-8">
            <div v-for="edu in education" :key="edu.school" class="relative pl-8">
                <div class="education-card">
                    <h3 class="text-xl font-bold text-white mb-1">
                        {{ props.lang === 'zh-tw' ? edu.school : edu.schoolEn }}
                    </h3>
                    <div class="text-blue-400 mb-1">
                        {{ props.lang === 'zh-tw' ? edu.department : edu.departmentEn }}
                    </div>
                    <div class="text-sm text-gray-400">
                        {{ props.lang === 'zh-tw' ? edu.period : edu.periodEn }}
                    </div>
                    <p v-if="props.lang === 'zh-tw' ? edu.description : edu.descriptionEn" 
                    class="text-sm text-gray-300 mt-2">
                        {{ props.lang === 'zh-tw' ? edu.description : edu.descriptionEn }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.education-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.education-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>