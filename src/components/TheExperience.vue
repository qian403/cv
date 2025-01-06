<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const experiences = computed(() => [
    {
        company: '愛普雲科技股份有限公司',
        companyEn: '愛普雲科技股份有限公司',
        department: '系統維運與安全部門',
        departmentEn: 'System Operations & Security',
        position: '實習工程師',
        positionEn: 'Intern Engineer',
        period: '2024-Current',
        periodEn: '2024-Present',
        duties: [
            // '參與系統開發與維護',
            // '協助網路架構規劃',
            // '執行資安檢測任務'
        ],
        dutiesEn: [
            // 'System development and maintenance',
            // 'Network architecture planning',
            // 'Security testing tasks'
        ]
    },
    {
        company: '一三五商行',
        companyEn: '135 Enterprise',
        department: '電腦部門',
        departmentEn: 'Computer Department',
        position: '實習網路管理工程師',
        positionEn: 'Network Management Engineer Intern',
        period: '2020-2023',
        periodEn: '2020-2023',
        duties: [
            // '網路設備維護與監控',
            // '系統故障排除',
            // '網路安全防護'
        ],
        dutiesEn: [
            // 'Network equipment maintenance and monitoring',
            // 'System troubleshooting',
            // 'Network security protection'
        ]
    }
])

const title = computed(() => props.lang === 'zh-tw' ? '工作經驗' : 'Work Experience')
</script>

<template>
    <section class="mb-12">
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>
        <div class="space-y-12">
            <div v-for="(exp, index) in experiences" :key="index" class="group relative pl-8">
                <!-- 時間軸裝飾 -->
                <div class="absolute left-0 top-0 h-full w-px bg-gray-700 group-hover:bg-blue-500 transition-colors duration-300"
                    :class="{ 'h-3/4': index === experiences.length - 1 }"></div>
                <div class="absolute left-0 top-2 w-3 h-3 rounded-full border-2 border-gray-700 bg-gray-900 -translate-x-[6px] group-hover:border-blue-500 group-hover:bg-blue-900 transition-colors duration-300">
                </div>

                <!-- 內容 -->
                <div class="relative experience-card">
                    <div class="mb-4">
                        <h3 class="text-xl font-bold text-white mb-1">
                            {{ props.lang === 'zh-tw' ? exp.position : exp.positionEn }}
                        </h3>
                        <div class="text-blue-400 mb-1">
                            {{ props.lang === 'zh-tw' ? exp.company : exp.companyEn }}
                        </div>
                        <div class="text-gray-500 text-sm mb-1">
                            {{ props.lang === 'zh-tw' ? exp.department : exp.departmentEn }}
                        </div>
                        <div class="text-gray-400 text-sm">
                            {{ props.lang === 'zh-tw' ? exp.period : exp.periodEn }}
                        </div>
                    </div>

                    <ul class="space-y-2 text-sm text-gray-300">
                        <li v-for="(duty, dutyIndex) in (props.lang === 'zh-tw' ? exp.duties : exp.dutiesEn)"
                            :key="dutyIndex" class="flex items-center space-x-2">
                            <span class="w-1.5 h-1.5 rounded-full bg-blue-500"></span>
                            <span>{{ duty }}</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.experience-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.experience-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>