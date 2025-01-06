<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const skills = computed(() => [
    {
        name: 'Network(IT)',
        nameZh: '網路技術',
        // level: '精通',
        description: '網路架構設計、網路安全、效能優化',
        descriptionEn: 'Network architecture design, network security, performance optimization'
    },
    {
        name: 'C++',
        nameZh: 'C++',
        // level: '熟練',
        description: '系統程式設計',
        descriptionEn: 'System programming'
    },
    {
        name: 'Linux/Windows Server',
        nameZh: 'Linux/Windows Server',
        // level: '精通',
        description: '伺服器維運、系統管理、服務部署',
        descriptionEn: 'Server operations, system administration, service deployment'
    },
    {
        name: 'Golang',
        nameZh: 'Golang',
        // level: '熟練',
        description: '後端開發、微服務架構',
        descriptionEn: 'Backend development, microservice architecture'
    },
    {
        name: 'Cybersecurity',
        nameZh: '資訊安全',
        // level: '熟練',
        description: '滲透測試、資安防護、弱點掃描',
        descriptionEn: 'Penetration testing, security protection, vulnerability scanning'
    }
])

const title = computed(() => props.lang === 'zh-tw' ? '專業技能' : 'Professional Skills')
</script>

<template>
    <section>
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>
        <div class="space-y-8">
            <div v-for="skill in skills" :key="skill.name" class="group relative pl-8">
                <!-- 裝飾元素 -->
                <div class="absolute left-0 top-0 h-full w-px bg-gray-700 group-hover:bg-blue-500 transition-colors duration-300"></div>
                <div class="absolute left-0 top-2 w-3 h-3 rounded-full border-2 border-gray-700 bg-gray-900 -translate-x-[6px] group-hover:border-blue-500 group-hover:bg-blue-900 transition-colors duration-300"></div>

                <!-- 內容卡片 -->
                <div class="skill-card">
                    <div class="mb-2">
                        <h3 class="text-xl font-bold text-white inline-block">
                            {{ props.lang === 'zh-tw' ? skill.nameZh : skill.name }}
                        </h3>
                        <span class="ml-4 text-sm text-gray-400">{{ skill.level }}</span>
                    </div>
                    <p class="text-sm text-gray-300">
                        {{ props.lang === 'zh-tw' ? skill.description : skill.descriptionEn }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.skill-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.skill-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>