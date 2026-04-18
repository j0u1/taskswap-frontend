<script lang="ts" setup>
definePageMeta({
    layout: "sidebar",
    pageTitle: "Участники",
});

const seoTitle = "Участники // TaskSwap";
const seoDescription =
    "Раздел TaskSwap с участниками команды, ролями, зонами ответственности и текущей загрузкой для удобного распределения задач.";

useSeoMeta({
    title: seoTitle,
    description: seoDescription,
    ogTitle: seoTitle,
    ogDescription: seoDescription,
    ogType: "website",
    ogSiteName: "TaskSwap",
    ogLocale: "ru_RU",
    twitterCard: "summary",
    twitterTitle: seoTitle,
    twitterDescription: seoDescription,
    robots: "noindex, nofollow, noarchive",
    keywords:
        "TaskSwap, участники, команда, сотрудники, пользователи, роли, ответственность, загрузка, dashboard, team",
});

useHead({
    htmlAttrs: {
        lang: "ru",
    },
    meta: [{ name: "theme-color", content: "#101012" }],
});
</script>

<template></template>
