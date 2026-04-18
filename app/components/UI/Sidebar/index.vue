<script lang="ts" setup>
import { padding } from "~/data/dynamicStyles";
import { pages } from "~/data/pages";

const route = useRoute();
const isCollapsed = ref(false);

console.log(route.path);
</script>

<template>
    <aside
        class="h-screen flex flex-col gap-4 duration-300 transition-all border-r border-border"
        :class="[isCollapsed ? 'w-19.75' : 'w-2/12 min-w-56']"
    >
        <UISidebarHead :is-collapsed="isCollapsed" />
        <hr class="h-0.5 w-full border-border" />
        <div class="space-y-3.5 px-3" :class="[isCollapsed && 'w-fit']">
            <NuxtLink
                v-for="page in pages"
                :key="page.title"
                :to="page.path"
                class="flex items-center gap-2 text-gray rounded-lg font-medium duration-200 transition-all whitespace-nowrap relative border"
                :class="[
                    route.path === page.path
                        ? 'border-transparent bg-secondary text-light-gray cursor-default'
                        : 'border-secondary hover:border-primary hover:text-primary',
                    isCollapsed ? 'size-12.75' : '',
                    padding,
                ]"
            >
                <component
                    :is="page.icon"
                    class="shrink-0 duration-300 transition-all"
                    :class="[
                        isCollapsed ? 'size-5 mx-auto my-2' : 'size-4.5',
                        route.path === page.path && 'delay-100',
                    ]"
                />
                <span
                    class="duration-200 transition-all origin-left"
                    :class="[
                        isCollapsed
                            ? 'scale-0 absolute opacity-0'
                            : 'relative scale-100',
                    ]"
                >
                    {{ page.title }}
                </span>
            </NuxtLink>
        </div>
    </aside>
</template>
