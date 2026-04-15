<script setup lang="ts">
definePageMeta({
    layout: "sidebar",
    pageTitle: "Обзор",
});

const statisticsOfCategories = [
    { name: "Оборудование", value: 2 },
    { name: "Сеть", value: 1 },
    { name: "ПО", value: 3 },
];
const maxValue = Math.max(...statisticsOfCategories.map((c) => c.value));
const getPercent = (value: number) => {
    if (!maxValue) return 0;
    return (value / maxValue) * 100 + "%";
};
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
        <UICard title="Статистика по категориям">
            <div class="flex flex-col gap-4">
                <div v-for="category in statisticsOfCategories" class="text-sm flex justify-between p-4 border border-border rounded-lg">
                    <div class="flex items-center justify-items-center gap-4 w-full">
                        <span class="uppercase text-gray w-38 truncate">{{ category.name }}</span>
                        <div class="w-full rounded-full h-2 bg-secondary overflow-hidden">
                            <div class="h-full bg-gray rounded-full" :style="{ width: getPercent(category.value) }" />
                        </div>
                        <span>{{ category.value }}</span>
                    </div>
                </div>
            </div>
        </UICard>
    </div>
</template>
