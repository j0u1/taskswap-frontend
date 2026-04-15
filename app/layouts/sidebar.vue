<script setup lang="ts">
const route = useRoute();

const pageTitle = computed(() => {
    return typeof route.meta.pageTitle === "string" ? route.meta.pageTitle : "Обзор";
});
</script>

<template>
    <div class="flex">
        <UISidebar class="hidden lg:flex" />

        <div class="flex flex-col gap-6 w-full">
            <DashboardHeading :title="pageTitle" />
            <hr class="h-0.5 w-full border-border" />
            <section class="px-4 lg:px-6 duration-300 transition-all size-full flex flex-col gap-6">
                <slot />
            </section>
        </div>
    </div>
</template>
