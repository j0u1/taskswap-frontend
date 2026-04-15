<script setup>
defineProps({
    title: String,
});
</script>

<template>
    <div class="relative flex flex-col gap-2 p-6 rounded-xl w-full bg-bg border border-border">
        <p v-if="title" class="uppercase text-gray">{{ title }}</p>
        <slot />
    </div>
</template>
