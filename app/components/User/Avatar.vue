<script setup lang="ts">
const props = defineProps({
    size: {
        type: [Number, String],
        default: 14,
    },
});

const normalizedSize = computed(() => {
    const size = Number(props.size);

    return Number.isFinite(size) && size > 0 ? size : 14;
});

const boxSize = computed(
    () => `calc(var(--spacing) * ${normalizedSize.value})`,
);
</script>

<template>
    <div
        class="select-none bg-primary text-black font-medium text-xl flex items-center justify-center rounded-full shrink-0"
        :style="{ width: boxSize, height: boxSize }"
    >
        Д
    </div>
</template>
