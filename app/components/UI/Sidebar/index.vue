<script lang="ts" setup>
import { Layout, Users2, PanelLeftClose, PanelLeftOpen, TriangleAlert } from "@lucide/vue";

const route = useRoute();
const isCollapsed = ref(false);
const pages = [
    { title: "Панель управления", path: "/dashboard", icon: Layout },
    { title: "Проблемы", path: "/tickets", icon: TriangleAlert },
    { title: "Сотрудники", path: "/employees", icon: Users2 },
];

console.log(route.path);
</script>

<template>
    <aside class="h-screen flex flex-col gap-4 duration-200 transition-all" :class="[isCollapsed ? 'w-19.75' : 'w-2/12 min-w-56']">
        <div
            class="relative flex justify-between items-center pt-6 duration-300 transition-all"
            :class="[isCollapsed ? 'px-4 pb-3.5' : 'px-4 pb-2']"
        >
            <NuxtLink class="duration-300 transition-all active:scale-105" :class="[isCollapsed ? 'mx-auto' : 'mx-0']" to="/">
                <IconsLogosFull v-if="!isCollapsed" />
                <IconsLogosMini class="size-6 max-h-6 shrink-0" v-else />
            </NuxtLink>
            <button
                @click="isCollapsed = !isCollapsed"
                class="absolute -right-4 bg-bg border border-border p-1.5 rounded-full text-gray hover:scale-102 cursor-pointer shrink-0 active:text-primary"
            >
                <PanelLeftClose v-if="!isCollapsed" class="size-4.5" />
                <PanelLeftOpen v-if="isCollapsed" class="size-4.5" />
            </button>
        </div>
        <hr class="h-0.5 w-full border-border" />
        <div class="space-y-3.5 px-3" :class="[isCollapsed && 'w-fit']">
            <NuxtLink
                v-for="page in pages"
                :key="page.title"
                :to="page.path"
                class="flex items-center gap-2 text-gray outline outline-secondary rounded-lg px-3 py-2 font-medium duration-200 transition-all whitespace-nowrap relative"
                :class="[
                    route.path === page.path ? 'bg-secondary text-light-gray cursor-default' : 'hover:outline-primary hover:text-primary',
                    isCollapsed ? 'size-12.75' : '',
                ]"
            >
                <component
                    :is="page.icon"
                    class="shrink-0 duration-300 transition-all"
                    :class="[isCollapsed ? 'size-5 mx-auto my-2' : 'size-4.5', route.path === page.path && 'delay-100']"
                />
                <span
                    class="duration-200 transition-all origin-left"
                    :class="[isCollapsed ? 'scale-0 absolute opacity-0' : 'relative scale-100']"
                >
                    {{ page.title }}
                </span>
            </NuxtLink>
        </div>
    </aside>
</template>
