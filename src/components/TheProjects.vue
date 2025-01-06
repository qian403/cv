<script setup>
import { computed } from 'vue'

const props = defineProps({
    lang: {
        type: String,
        required: true
    }
})

const projects = computed(() => [
    // {
    //     name: 'Network Management System',
    //     nameZh: '網路管理系統',
    //     description: '基於 Go 的網路設備監控與管理系統，支援 SNMP 協議和自動化配置',
    //     descriptionEn: 'Go-based network device monitoring and management system with SNMP support and automated configuration',
    //     tech: ['Golang', 'Vue.js', 'PostgreSQL', 'Docker'],
    //     github: 'https://github.com/yourusername/network-management',
    //     demo: 'https://demo.example.com/network-management'
    // },


])

const title = computed(() => props.lang === 'zh-tw' ? '專案作品' : 'Projects')
</script>
<template>
    <section class="relative"> <!-- Add relative positioning to section -->
        <h2 class="text-2xl font-bold mb-8 text-white">{{ title }}</h2>

        <!-- Single timeline decoration for all items -->
        <div class="absolute left-0 top-0 bottom-0 w-px bg-gray-700"></div>

        <div class="space-y-8">
            <div v-for="project in projects" :key="project.name" class="group ml-8">
                <!-- Use margin instead of padding -->
                <!-- Just the dot decoration for each item -->
                <div
                    class="absolute -left-8 top-2 w-3 h-3 rounded-full border-2 border-gray-700 bg-gray-900 -translate-x-[6px] group-hover:border-blue-500 group-hover:bg-blue-900 transition-colors duration-300">
                </div>

                <div class="project-card">
                    <!-- Project title -->
                    <h3 class="text-xl font-bold text-white mb-2">
                        {{ props.lang === 'zh-tw' ? project.nameZh : project.name }}
                    </h3>

                    <!-- Links -->
                    <div class="flex gap-3 mb-3">
                        <a v-if="project.demo" :href="project.demo" target="_blank"
                            class="text-sm text-blue-400 hover:text-blue-300 transition-colors duration-100">
                            Demo →
                        </a>
                        <a :href="project.github" target="_blank"
                            class="text-sm text-gray-400 hover:text-gray-300 transition-colors duration-200">
                            GitHub →
                        </a>
                    </div>

                    <!-- Description -->
                    <p class="text-sm text-gray-300 mb-3">
                        {{ props.lang === 'zh-tw' ? project.description : project.descriptionEn }}
                    </p>

                    <!-- Technologies -->
                    <div class="flex flex-wrap gap-2">
                        <span v-for="tech in project.tech" :key="tech"
                            class="px-2 py-1 text-xs text-gray-300 bg-gray-800 rounded-full">
                            {{ tech }}
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
.project-card {
    transition: all 0.3s ease;
    padding: 16px;
    border-radius: 8px;
}

.project-card:hover {
    background: rgba(30, 41, 59, 0.5);
    transform: translateX(8px);
}
</style>