<script lang="ts" setup>
import { LayoutIcon, TicketIcon, Users2Icon, PanelLeftCloseIcon, PanelLeftOpenIcon } from "@lucide/vue";

const route = useRoute();
const isCollapsed = ref(false);
const pages = [
    { title: "Панель управления", path: "/dashboard", icon: LayoutIcon },
    { title: "Тикеты", path: "/tickets", icon: TicketIcon },
    { title: "Сотрудники", path: "/employees", icon: Users2Icon },
];

console.log(route.path);
</script>

<template>
    <aside class="h-screen flex flex-col gap-4 w-2/12 duration-200 transition-all" :class="{ 'w-21': isCollapsed }">
        <div class="flex justify-between items-center pt-4" :class="[isCollapsed ? 'pl-4 pr-2 pb-1' : 'px-4']">
            <NuxtLink class="duration-300 transition-all active:scale-105" to="/">
                <IconsLogosFull v-if="!isCollapsed" />
                <IconsLogosMini class="size-6 max-h-6 shrink-0 mt-0.75" v-else />
            </NuxtLink>
            <button @click="isCollapsed = !isCollapsed" class="mt-1 text-gray hover:scale-102 cursor-pointer shrink-0 active:text-primary">
                <PanelLeftCloseIcon v-if="!isCollapsed" class="size-4.5" />
                <PanelLeftOpenIcon v-if="isCollapsed" class="size-4.5" />
            </button>
        </div>
        <hr class="h-0.5 w-full border-border" />
        <div class="space-y-3.5 px-3">
            <NuxtLink
                v-for="page in pages"
                :key="page.title"
                :to="page.path"
                class="flex items-center gap-2 text-gray outline outline-additional rounded-lg py-2 px-2.5 font-medium duration-200 transition-all whitespace-nowrap relative"
                :class="[
                    route.path === page.path ? 'bg-additional text-primary cursor-default' : 'hover:outline-primary',
                    isCollapsed ? 'size-12.75' : '',
                ]"
            >
                <component
                    :is="page.icon"
                    class="shrink-0 duration-300 transition-all delay-100"
                    :class="[isCollapsed ? 'size-5 mx-auto my-2' : 'size-4.5']"
                />
                <span
                    class="duration-200 transition-all origin-left"
                    :class="[isCollapsed ? 'scale-0 absolute opacity-0' : 'relative scale-100']"
                    >{{ page.title }}</span
                >
            </NuxtLink>
        </div>
    </aside>
</template>
