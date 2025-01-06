<script setup>
import { computed } from "vue";

const props = defineProps({
    lang: {
        type: String,
        required: true,
    },
});

const personalInfo = computed(() => ({
    name: props.lang === "zh-tw" ? "徐嘉謙" : "Chia-Chien Hsu",
    email: "qian@qian30.net",
    blog: "blog.qian30.net",
    telegram: "@qian50",
}));
</script>

<template>
    <header class="mb-8">
        <h1 class="text-4xl font-bold mb-4 text-white">{{ personalInfo.name }}</h1>
        <div class="flex flex-wrap gap-4">
            <a :href="'mailto:' + personalInfo.email"
                class="flex items-center text-gray-300 hover:text-blue-400 transition-colors duration-200">
                <i class="fas fa-envelope mr-2.5"></i>
                {{ personalInfo.email }}
            </a>
            <a :href="'https://' + personalInfo.blog" target="_blank"
                class="flex items-center text-gray-300 hover:text-blue-400 transition-colors duration-200">
                <i class="fas fa-globe mr-2.5"></i>
                {{ personalInfo.blog }}
            </a>
            <a :href="'https://t.me/' + personalInfo.telegram" target="_blank"
                class="flex items-center text-gray-300 hover:text-blue-400 transition-colors duration-200">
                <i class="fab fa-telegram mr-2.5"></i>
                {{ personalInfo.telegram }}
            </a>
        </div>
    </header>
</template>