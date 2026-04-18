<script setup lang="ts">
import type { LucideIcon } from "@lucide/vue";

withDefaults(
    defineProps<{
        title?: string;
        button?: {
            boolean: boolean;
            text?: string;
        };
        icon?: LucideIcon;
    }>(),
    {
        button: () => ({
            boolean: false,
        }),
    },
);
</script>

<template>
    <div class="relative flex flex-col gap-4 p-4 rounded-xl w-full bg-bg border border-border h-fit">
        <div v-if="title || button.boolean" class="flex items-center" :class="!title && button.boolean ? 'justify-end' : 'justify-between'">
            <p v-if="title" class="uppercase text-gray">{{ title }}</p>
            <button class="flex items-center gap-1.5 text-light-gray transition-all hover:border-primary hover:text-primary cursor-pointer">
                <component :is="icon" class="size-4" />
                <span v-if="button.boolean && button.text" class="text-sm">
                    {{ button.text }}
                </span>
            </button>
        </div>
        <slot />
    </div>
</template>
