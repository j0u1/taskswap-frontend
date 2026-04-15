<script setup lang="ts">
definePageMeta({
    layout: "sidebar",
    pageTitle: "Обзор",
});
</script>

<template>
    <DashboardProblems />
    <div class="flex gap-6">
        <UICard title="Последние проблемы">
            <div class="flex flex-col gap-4">
                <div class="text-sm flex justify-between p-4 border border-border rounded-lg">
                    <div class="flex gap-4">
                        <span class="uppercase text-gray">прб-0042</span>
                        <p class="text-light-gray max-w-100 truncate">Не работает внутренний прокси, после обновления Windows</p>
                    </div>
                </div>
            </div>
        </UICard>
        <UICard> </UICard>
    </div>
</template>
